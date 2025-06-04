<template>
  <v-container fluid class="py-8">
    <div v-if="!currentUnit" class="welcome-screen">
      <v-row justify="center">
        <v-col cols="12" sm="10" md="8" lg="6">
          <v-card class="welcome-card pa-6" variant="elevated" rounded="xl">
            <div class="text-center mb-6">
              <v-img
                src="@/assets/logo.png"
                height="120"
                contain
                class="mb-6"
              ></v-img>
              <h1 class="text-h3 font-weight-bold primary--text mb-2">AP Calculus Review</h1>
              <p class="text-h6 text-grey">Your comprehensive guide to AP Calculus concepts</p>
            </div>

            <v-divider class="mb-6"></v-divider>

            <p class="text-body-1 mb-6">
              Welcome to your interactive AP Calculus review resource. This platform organizes essential 
              calculus concepts and formulas into the units that align with the AP Calculus curriculum.
              Select a unit from the sidebar to begin your review.
            </p>

            <v-row>
              <v-col v-for="(unit, i) in units.slice(0, 4)" :key="i" cols="6" md="3">
                <v-card
                  :color="unit.color"
                  height="100"
                  @click="$emit('update:currentUnit', unit)"
                  class="d-flex align-center justify-center unit-card"
                  dark
                  hover
                  rounded="lg"
                >
                  <div class="text-center">
                    <v-icon size="x-large" class="mb-2">{{ unit.icon }}</v-icon>
                    <div class="text-caption font-weight-medium">Unit {{ i + 1 }}</div>
                  </div>
                </v-card>
              </v-col>
            </v-row>

            <v-divider class="my-6"></v-divider>

            <h2 class="text-h5 font-weight-bold mb-4">About This Resource</h2>
            <v-row>
              <v-col cols="12" md="4">
                <v-card variant="outlined" class="pa-4" rounded="lg">
                  <div class="d-flex align-center mb-2">
                    <v-icon color="primary" class="me-2">mdi-calculator</v-icon>
                    <h3 class="text-h6">Complete Coverage</h3>
                  </div>
                  <p class="text-body-2">All units and topics from the AP Calculus curriculum</p>
                </v-card>
              </v-col>
              <v-col cols="12" md="4">
                <v-card variant="outlined" class="pa-4" rounded="lg">
                  <div class="d-flex align-center mb-2">
                    <v-icon color="primary" class="me-2">mdi-formula</v-icon>
                    <h3 class="text-h6">Key Formulas</h3>
                  </div>
                  <p class="text-body-2">Essential formulas presented in mathematical notation</p>
                </v-card>
              </v-col>
              <v-col cols="12" md="4">
                <v-card variant="outlined" class="pa-4" rounded="lg">
                  <div class="d-flex align-center mb-2">
                    <v-icon color="primary" class="me-2">mdi-lightbulb-outline</v-icon>
                    <h3 class="text-h6">Core Concepts</h3>
                  </div>
                  <p class="text-body-2">Explanations of fundamental calculus concepts</p>
                </v-card>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </v-row>
    </div>

    <div v-else>
      <v-breadcrumbs :items="[
        { title: 'Home', disabled: false },
        { title: currentUnit.title, disabled: true },
      ]"></v-breadcrumbs>

      <v-card variant="outlined" rounded="xl" class="mb-6">
        <div class="d-flex flex-column flex-md-row">
          <div class="unit-header pa-6" :style="\`background-color: \${currentUnit.color}20;\`">
            <v-avatar 
              size="64" 
              :color="currentUnit.color" 
              class="mb-4"
            >
              <v-icon size="32" color="white">{{ currentUnit.icon }}</v-icon>
            </v-avatar>
            <h2 class="text-h4 font-weight-bold mb-2">{{ currentUnit.title }}</h2>
            <p class="text-subtitle-1 text-medium-emphasis">
              Review key concepts and formulas in this unit
            </p>
          </div>
          <v-img
            :src="currentUnit.image"
            max-width="300"
            contain
            class="d-none d-md-flex align-self-center mx-auto my-4"
          ></v-img>
        </div>
      </v-card>

      <v-row>
        <v-col cols="12" md="7">
          <v-card rounded="lg" class="mb-6" elevation="1">
            <v-card-title class="text-h5 py-4 px-6 d-flex align-center">
              <v-icon color="primary" class="me-2" size="large">mdi-function-variant</v-icon>
              Key Formulas
            </v-card-title>
            <v-divider></v-divider>
            <v-expansion-panels variant="accordion">
              <v-expansion-panel
                v-for="(formula, i) in currentUnit.formulas"
                :key="i"
                rounded="0"
              >
                <v-expansion-panel-title class="text-subtitle-1 font-weight-medium">
                  {{ formula.name }}
                </v-expansion-panel-title>
                <v-expansion-panel-text>
                  <div class="formula-box pa-4 rounded bg-surface-variant">
                    {{ formula.formula }}
                  </div>
                </v-expansion-panel-text>
              </v-expansion-panel>
            </v-expansion-panels>
          </v-card>
        </v-col>

        <v-col cols="12" md="5">
          <v-card rounded="lg" elevation="1">
            <v-card-title class="text-h5 py-4 px-6 d-flex align-center">
              <v-icon color="primary" class="me-2" size="large">mdi-lightbulb-outline</v-icon>
              Key Concepts
            </v-card-title>
            <v-divider></v-divider>
            <v-list lines="two">
              <v-list-item
                v-for="(concept, i) in currentUnit.concepts"
                :key="i"
                class="py-2"
              >
                <template v-slot:prepend>
                  <v-avatar size="32" :color="currentUnit.color" class="me-3">
                    <span class="text-caption text-white font-weight-bold">{{ i + 1 }}</span>
                  </v-avatar>
                </template>
                <v-list-item-title class="text-subtitle-1 font-weight-medium">
                  {{ concept }}
                </v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card>
        </v-col>
      </v-row>
    </div>
  </v-container>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

defineProps({
  currentUnit: Object,
  units: Array
});

defineEmits(['update:currentUnit']);
</script>

<style scoped>
.welcome-card {
  background: linear-gradient(to bottom right, rgba(255,255,255,0.9), rgba(255,255,255,0.8));
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255,255,255,0.2);
}

.unit-card {
  transition: transform 0.3s;
}

.unit-card:hover {
  transform: translateY(-5px);
}

.unit-header {
  border-radius: 12px 0 0 12px;
}

.formula-box {
  font-family: 'Georgia', serif;
  font-style: italic;
  font-size: 1.1rem;
  line-height: 1.7;
}

@media (max-width: 600px) {
  .unit-header {
    border-radius: 12px 12px 0 0;
  }
}
</style>
