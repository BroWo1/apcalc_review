<template>
  <v-container class="pa-0 bg-grey-lighten-4" style="min-height: 100vh;" fluid>
    <v-row justify="center" align="start" style="min-height: inherit;" class="py-md-6">
      <v-col cols="12" md="11" lg="9" xl="8">
        <v-sheet rounded="xl" class="pa-5 pa-md-10 my-0 my-md-6" elevation="4">
          <div class="text-center mb-10 mb-md-12">
            <h1 class="text-h3 text-md-h2 font-weight-bold mb-3 text-grey-darken-3">
              AP Calculus Review
            </h1>
            <p class="text-h6 text-md-h5 font-weight-regular text-grey-darken-1 mb-8">
              Your comprehensive guide to mastering AP Calculus AB
            </p>
            
            <div class="d-flex justify-center">
              <SearchBar 
                class="mx-auto"
                max-width="500px"
                variant="solo-filled"
                :rounded="true"
                :flat="true"
                label="Search topics..."
                prepend-inner-icon="mdi-magnify"
              />
            </div>
          </div>
          
          <v-row>
            <v-col cols="12" sm="6" v-for="unit in units" :key="unit.id" class="d-flex">
              <v-card
                class="unit-card d-flex flex-column"
                :color="unit.color"
                variant="elevated"
                elevation="2"
                rounded="lg"
                height="100%"
                hover
                @click="navigateTo(unit.path)"
              >
                <v-card-title class="text-h5 font-weight-medium text-white">{{ unit.title }}</v-card-title>
                <v-card-text class="flex-grow-1">
                  <p class="mb-4 text-white">{{ unit.description }}</p>
                  <div class="key-topics">
                    <v-chip 
                      v-for="topic in unit.keyTopics" 
                      :key="topic" 
                      class="ma-1" 
                      size="small" 
                      color="white"
                      variant="outlined"
                    >
                      {{ topic }}
                    </v-chip>
                  </div>
                </v-card-text>
                <v-card-actions class="pa-4">
                  <v-btn 
                    color="white" 
                    variant="flat" 
                    block 
                    rounded="md"
                    :ripple="false"
                    @click.stop="navigateTo(unit.path)"
                  >
                    <span :class="`text-${unit.color} font-weight-bold`">Start {{ unit.name }}</span>
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
          
          <div class="mt-12">
            <h2 class="text-h4 font-weight-bold mb-6 text-grey-darken-3">Quick Resources</h2>
            <v-row>
              <v-col cols="12" md="4" v-for="resource in quickResources" :key="resource.title" class="d-flex">
                <v-card class="d-flex flex-column" variant="outlined" rounded="lg" height="100%">
                  <v-card-title class="d-flex align-center">
                    <v-icon :icon="resource.icon" class="mr-3" color="primary"></v-icon>
                    <span class="text-h6 font-weight-medium">{{ resource.title }}</span>
                  </v-card-title>
                  <v-card-text class="flex-grow-1">
                    {{ resource.text }}
                  </v-card-text>
                  <v-card-actions class="pa-4">
                    <v-btn 
                      variant="tonal" 
                      color="primary" 
                      block 
                      rounded="md"
                      @click="navigateTo(resource.path)"
                    >
                      {{ resource.actionText }}
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-col>
            </v-row>
          </div>
        </v-sheet>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import SearchBar from '@/components/SearchBar.vue';

const router = useRouter();

const navigateTo = (path) => {
  router.push(path);
};

const units = ref([
  { 
    id: 1, 
    name: 'Unit 1', 
    title: 'Limits & Continuity', 
    description: 'Master the foundational concepts of calculus including one-sided and two-sided limits, asymptotic behavior, and the precise definition of continuity. Learn to evaluate limits algebraically and graphically while understanding removable and non-removable discontinuities.', 
    keyTopics: ['Graphical Limits', 'Algebraic Limits', 'Squeeze Theorem', 'Asymptotes', 'Continuity Tests', 'IVT'], 
    path: '/units/limits', 
    color: 'blue-darken-2' 
  },
  { 
    id: 2, 
    name: 'Unit 2', 
    title: 'Intro to Derivatives', 
    description: 'Explore the derivative as the limit of difference quotients and develop fluency with basic differentiation rules. Connect derivatives to rates of change and slopes of tangent lines while mastering power, product, and quotient rules.', 
    keyTopics: ['Difference Quotients', 'Power Rule', 'Product Rule', 'Quotient Rule', 'Tangent Lines', 'Instantaneous Rate'], 
    path: '/units/differentiation-definition-properties', 
    color: 'teal-darken-2' 
  },
  { 
    id: 3, 
    name: 'Unit 3', 
    title: 'Derivative Techniques', 
    description: 'Master advanced differentiation techniques including the chain rule for composite functions, implicit differentiation for related variables, and derivatives of inverse functions including logarithmic and exponential functions.', 
    keyTopics: ['Chain Rule', 'Implicit Differentiation', 'Inverse Functions', 'Logarithmic Differentiation', 'Exponential Functions', 'Trigonometric Derivatives'], 
    path: '/units/differentiation-composite-implicit-inverse', 
    color: 'blue-darken-2' 
  },
  { 
    id: 4, 
    name: 'Unit 4', 
    title: 'Applications of Derivatives', 
    description: 'Apply derivatives to solve real-world problems involving related rates, motion analysis, and optimization. Learn L\'Hôpital\'s rule for evaluating indeterminate forms and interpret derivatives in various contexts.', 
    keyTopics: ['Related Rates', 'L\'Hôpital\'s Rule', 'Position/Velocity/Acceleration', 'Linear Approximation', 'Differentials', 'Indeterminate Forms'], 
    path: '/units/contextual-applications-differentiation', 
    color: 'teal-darken-2' 
  },
  { 
    id: 5, 
    name: 'Unit 5', 
    title: 'Analyzing with Derivatives', 
    description: 'Use first and second derivatives to analyze function behavior including intervals of increase/decrease, concavity, and critical points. Apply the Mean Value Theorem and solve optimization problems with constraints.', 
    keyTopics: ['Critical Points', 'First Derivative Test', 'Second Derivative Test', 'Concavity', 'Mean Value Theorem', 'Optimization'], 
    path: '/units/analytical-applications-differentiation', 
    color: 'blue-darken-2' 
  },
  { 
    id: 6, 
    name: 'Unit 6', 
    title: 'Intro to Integrals', 
    description: 'Discover integration as the reverse of differentiation and understand definite integrals as the limit of Riemann sums. Master the Fundamental Theorem of Calculus and basic integration techniques including substitution.', 
    keyTopics: ['Riemann Sums', 'Fundamental Theorem', 'Antiderivatives', 'Definite Integrals', 'u-Substitution', 'Net Change'], 
    path: '/units/integration-accumulation-change', 
    color: 'teal-darken-2' 
  },
  { 
    id: 7, 
    name: 'Unit 7', 
    title: 'Differential Equations', 
    description: 'Learn to solve separable differential equations and interpret slope fields. Apply differential equations to model exponential growth and decay, logistic growth, and other dynamic systems in real-world contexts.', 
    keyTopics: ['Separable DEs', 'Slope Fields', 'Exponential Growth', 'Exponential Decay', 'Logistic Growth', 'Euler\'s Method'], 
    path: '/units/differential-equations', 
    color: 'blue-darken-2' 
  },
  { 
    id: 8, 
    name: 'Unit 8', 
    title: 'Applications of Integrals', 
    description: 'Apply integration to find areas between curves, volumes of solids of revolution using disk and washer methods, and analyze accumulation functions. Solve problems involving average value and motion with variable acceleration.', 
    keyTopics: ['Area Between Curves', 'Disk Method', 'Washer Method', 'Cross Sections', 'Average Value', 'Accumulation Functions'], 
    path: '/units/applications-integration', 
    color: 'teal-darken-2' 
  },
]);

const quickResources = ref([
  { title: 'Formula Sheet', icon: 'mdi-calculator-variant-outline', text: 'Access all essential formulas for the AP Calculus exam in one convenient place.', actionText: 'View Formulas', path: '/formula' },
  { title: 'Practice Problems', icon: 'mdi-pencil-outline', text: 'Test your understanding with topic-specific practice problems and full-length exams.', actionText: 'Start Practice', path: '/practice' },
]);

</script>

<style scoped>
.unit-card {
  transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
  cursor: pointer;
  will-change: transform, box-shadow;
}

.unit-card:hover {
  transform: translateY(-8px) scale(1.02);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15), 0 16px 16px rgba(0, 0, 0, 0.12);
}

.unit-card:active {
  transform: translateY(-4px) scale(1.01);
  transition: all 0.1s cubic-bezier(0.25, 0.8, 0.25, 1);
}

/* Ensure chips have proper contrast on colored backgrounds */
.v-chip {
  backdrop-filter: blur(8px);
  background-color: rgba(255, 255, 255, 0.15) !important;
}

.v-chip .v-chip__content {
  color: white !important;
  font-weight: 500;
}

.key-topics {
  margin-top: 16px;
}

/* Ensure card actions are at the bottom if content is short */
.v-card {
  display: flex;
  flex-direction: column;
}

.v-card-text {
  flex-grow: 1;
}

/* Hover effect for the action button */
.unit-card:hover .v-btn {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  transform: translateY(-2px);
}

.v-btn {
  transition: all 0.2s cubic-bezier(0.25, 0.8, 0.25, 1);
}

/* Customizing scrollbar for a cleaner look if content overflows the sheet */
.v-sheet {
  overflow-y: auto;
}

/* For Webkit browsers like Chrome, Safari */
.v-sheet::-webkit-scrollbar {
  width: 8px;
}

.v-sheet::-webkit-scrollbar-track {
  background: transparent; 
}

.v-sheet::-webkit-scrollbar-thumb {
  background-color: rgba(0,0,0,0.2);
  border-radius: 4px;
}

.v-sheet::-webkit-scrollbar-thumb:hover {
  background-color: rgba(0,0,0,0.3);
}

/* Improve text readability on colored backgrounds */
.v-card-title,
.v-card-text p {
  text-shadow: 0 1px 3px rgba(0, 0, 0, 0.3);
}

/* Ensure proper spacing and typography */
.v-card-title {
  line-height: 1.3;
  padding-bottom: 8px;
}

.v-card-text p {
  line-height: 1.5;
  opacity: 0.95;
}
</style>
