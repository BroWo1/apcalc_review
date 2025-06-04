<template>
  <v-container class="pa-0 bg-grey-lighten-4" style="min-height: 100vh;" fluid>
    <v-row justify="center" align="start" style="min-height: inherit;" class="py-md-6">
      <v-col cols="12" md="11" lg="10" xl="9">
        <v-sheet rounded="xl" class="pa-5 pa-md-10 my-0 my-md-6" elevation="4">
          <div class="text-center mb-8">
            <h1 class="text-h3 text-md-h2 font-weight-bold mb-3 text-grey-darken-3">
              Practice Problems
            </h1>
            <p class="text-h6 text-md-h5 font-weight-regular text-grey-darken-1 mb-6">
              AP Calculus AB Past Exams
            </p>
          </div>

          <!-- Year Selection Tabs -->
          <v-tabs 
            v-model="selectedYear" 
            centered 
            color="primary" 
            class="mb-8"
            density="compact"
          >
            <v-tab v-for="year in availableYears" :key="year" :value="year" class="text-h6">
              {{ year }}
            </v-tab>
          </v-tabs>

          <!-- Exam Type Selection -->
          <v-row class="mb-6" v-if="getAvailableExamTypes().length > 0">
            <v-col cols="12" sm="6" md="3" v-for="examType in getAvailableExamTypes()" :key="examType.id">
              <v-card
                :color="selectedExamType === examType.id ? examType.color : 'grey-lighten-3'"
                :variant="selectedExamType === examType.id ? 'flat' : 'outlined'"
                rounded="lg"
                hover
                @click="selectExamType(examType.id)"
                class="text-center pa-4 exam-type-card"
                height="120"
              >
                <v-icon 
                  :icon="examType.icon" 
                  size="36" 
                  :color="selectedExamType === examType.id ? 'white' : 'grey-darken-2'"
                  class="mb-2"
                ></v-icon>
                <v-card-title 
                  class="text-subtitle-1 font-weight-bold" 
                  :class="selectedExamType === examType.id ? 'text-white' : 'text-grey-darken-2'"
                >
                  {{ examType.title }}
                </v-card-title>
              </v-card>
            </v-col>
          </v-row>

          <!-- No Exams Available Alert -->
          <v-alert 
            v-if="getAvailableExamTypes().length === 0" 
            type="info" 
            variant="tonal" 
            class="mb-6"
          >
            <v-icon icon="mdi-information" class="mr-2"></v-icon>
            No exam files available for {{ selectedYear }}. Please check back later or try a different year.
          </v-alert>

          <!-- PDF Viewer -->
          <v-card v-if="selectedExamType && getCurrentPdfUrl()" rounded="lg" elevation="2">
            <v-card-title class="bg-primary text-white pa-6 d-flex justify-space-between align-center">
              <div class="d-flex align-center">
                <v-icon icon="mdi-file-pdf-box" class="mr-3"></v-icon>
                {{ selectedYear }} AP Calculus AB - {{ getCurrentExamType().title }}
              </div>
              <div class="d-flex align-center">
                <v-btn
                  :href="getCurrentPdfUrl()"
                  target="_blank"
                  color="white"
                  variant="outlined"
                  size="small"
                  class="mr-2"
                >
                  <v-icon icon="mdi-open-in-new" class="mr-2"></v-icon>
                  Open in New Tab
                </v-btn>
                <v-btn
                  :href="getCurrentPdfUrl()"
                  :download="getCurrentPdfFilename()"
                  color="white"
                  variant="outlined"
                  size="small"
                >
                  <v-icon icon="mdi-download" class="mr-2"></v-icon>
                  Download
                </v-btn>
              </div>
            </v-card-title>

            <v-card-text class="pa-0">
              <div class="pdf-container">
                <iframe
                  :src="getCurrentPdfUrl()"
                  class="pdf-viewer"
                  frameborder="0"
                  type="application/pdf"
                >
                  <div class="pdf-fallback pa-6 text-center">
                    <v-icon icon="mdi-file-pdf-box" size="48" color="error" class="mb-4"></v-icon>
                    <h3 class="text-h6 mb-3">PDF Viewer Not Available</h3>
                    <p class="text-body-2 mb-4">Your browser doesn't support inline PDF viewing.</p>
                    <v-btn
                      :href="getCurrentPdfUrl()"
                      target="_blank"
                      color="primary"
                      variant="flat"
                      class="mr-2"
                    >
                      <v-icon icon="mdi-open-in-new" class="mr-2"></v-icon>
                      Open PDF
                    </v-btn>
                    <v-btn
                      :href="getCurrentPdfUrl()"
                      :download="getCurrentPdfFilename()"
                      color="primary"
                      variant="outlined"
                    >
                      <v-icon icon="mdi-download" class="mr-2"></v-icon>
                      Download PDF
                    </v-btn>
                  </div>
                </iframe>
              </div>
            </v-card-text>
          </v-card>

          <!-- No Selection State -->
          <v-card v-else-if="getAvailableExamTypes().length > 0" rounded="lg" elevation="2" class="text-center pa-12">
            <v-icon icon="mdi-file-question-outline" size="64" color="grey-lighten-1" class="mb-4"></v-icon>
            <h3 class="text-h5 font-weight-medium text-grey-darken-1 mb-2">
              Select an Exam Type
            </h3>
            <p class="text-body-1 text-grey-darken-1">
              Choose an exam type to view the PDF
            </p>
          </v-card>
        </v-sheet>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue';

// Reactive data
const selectedYear = ref('2017');
const selectedExamType = ref(null);
const availableYears = ref([]);
const availableExams = ref({});

// Exam type mappings to PDF filenames
const examTypeMapping = {
  'mcq': { 
    title: 'Multiple Choice Questions', 
    icon: 'mdi-format-list-bulleted-square', 
    color: 'blue-darken-2',
    filename: 'mcq.pdf'
  },
  'mcq-answers': { 
    title: 'MCQ Answer Key', 
    icon: 'mdi-check-circle-outline', 
    color: 'green-darken-2',
    filename: 'mcq-answers.pdf'
  },
  'frq': { 
    title: 'Free Response Questions', 
    icon: 'mdi-pencil-outline', 
    color: 'purple-darken-2',
    filename: 'frq.pdf'
  },
  'frq-answers': { 
    title: 'FRQ Scoring Guidelines', 
    icon: 'mdi-file-check-outline', 
    color: 'orange-darken-2',
    filename: 'frq-scoring-guidelines.pdf'
  },
};

// PDF file mappings based on actual file structure
const examFiles = ref({
  '2017': {
    'mcq': '/exams/2017/ap-calculus-ab-2017-international-practice-exam-mcq.pdf',
    'mcq-answers': '/exams/2017/ap-calculus-ab-2017-international-practice-exam-mcq-answers.pdf',
    'frq': '/exams/2017/ap-calculus-ab-2017-international-practice-exam-frq.pdf',
    'frq-answers': '/exams/2017/ap-calculus-ab-2017-international-practice-exam-frq-scoring-guidelines.pdf'
  },
  '2018': {
    'mcq': '/exams/2018/ap-calculus-ab-2018-international-practice-exam-mcq.pdf',
    'mcq-answers': '/exams/2018/ap-calculus-ab-2018-international-practice-exam-mcq-answers.pdf',
    'frq': '/exams/2018/ap-calculus-ab-2018-international-practice-exam-frq.pdf',
    'frq-answers': '/exams/2018/ap-calculus-ab-2018-international-practice-exam-frq-scoring-guidelines.pdf'
  },
  '2019': {
    'mcq': '/exams/2019/ap-calculus-ab-2019-practice-exam-mcq.pdf',
    'mcq-answers': '/exams/2019/ap-calculus-ab-2019-international-practice-exam-mcq-answers.pdf',
    'frq': '/exams/2019/ap-calculus-ab-2019-practice-exam-frq.pdf',
    'frq-answers': '/exams/2019/ap-calculus-ab-2019-international-practice-exam-frq-scoring-guidelines.pdf'
  }
});

// Initialize available years based on what has files
onMounted(() => {
  availableYears.value = Object.keys(examFiles.value).filter(year => 
    Object.keys(examFiles.value[year]).length > 0
  );
  
  // Set first available year as default
  if (availableYears.value.length > 0) {
    selectedYear.value = availableYears.value[0];
  }
});

// Methods
const selectExamType = (type) => {
  selectedExamType.value = type;
};

const getCurrentExamType = () => {
  return examTypeMapping[selectedExamType.value] || {};
};

const getAvailableExamTypes = () => {
  const yearFiles = examFiles.value[selectedYear.value] || {};
  return Object.keys(yearFiles).map(typeId => ({
    id: typeId,
    ...examTypeMapping[typeId]
  }));
};

const getCurrentPdfUrl = () => {
  const yearFiles = examFiles.value[selectedYear.value] || {};
  return yearFiles[selectedExamType.value] || null;
};

const getCurrentPdfFilename = () => {
  if (!selectedExamType.value || !selectedYear.value) return '';
  
  const examType = examTypeMapping[selectedExamType.value];
  if (!examType) return '';
  
  return `AP-Calculus-AB-${selectedYear.value}-${examType.filename}`;
};
</script>

<style scoped>
.exam-type-card {
  transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
  cursor: pointer;
}

.exam-type-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15);
}

/* PDF Viewer Styles */
.pdf-container {
  position: relative;
  width: 100%;
  height: 80vh;
  min-height: 600px;
  border-radius: 0 0 12px 12px;
  overflow: hidden;
}

.pdf-viewer {
  width: 100%;
  height: 100%;
  border: none;
  background-color: #f5f5f5;
}

.pdf-fallback {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100%;
  background-color: #f9f9f9;
  border: 2px dashed #ddd;
  border-radius: 8px;
}

/* Responsive design improvements */
@media (max-width: 960px) {
  .pdf-container {
    height: 70vh;
    min-height: 500px;
  }
}

@media (max-width: 600px) {
  .v-sheet {
    margin: 0 !important;
    border-radius: 0 !important;
  }
  
  .exam-type-card {
    height: auto !important;
    min-height: 100px;
  }
  
  .pdf-container {
    height: 60vh;
    min-height: 400px;
  }
}

/* Ensure proper button spacing in card title */
.v-card-title .v-btn {
  margin-left: 8px;
}

.v-card-title .v-btn:first-of-type {
  margin-left: 0;
}

/* Loading states and error handling */
.pdf-viewer:not([src]) {
  background: linear-gradient(90deg, #f0f0f0 25%, #e0e0e0 50%, #f0f0f0 75%);
  background-size: 200% 100%;
  animation: loading 1.5s infinite;
}

@keyframes loading {
  0% {
    background-position: 200% 0;
  }
  100% {
    background-position: -200% 0;
  }
}

/* Improve text readability */
.v-card-title {
  line-height: 1.3;
}

/* Ensure proper spacing and alignment */
.d-flex.justify-space-between .v-btn {
  white-space: nowrap;
}

/* Tab styling improvements */
.v-tabs {
  border-radius: 8px;
  background-color: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(8px);
}

/* Alert styling */
.v-alert {
  border-radius: 12px;
}

/* Card improvements */
.v-card {
  transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
}

.v-card:hover {
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
}
</style>
