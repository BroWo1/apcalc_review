<template>
  <v-app>
    <v-navigation-drawer
      app
      v-model="drawer"
      :permanent="!mobile"
      :temporary="mobile"
      color="surface"
      width="300" 
    >
      <v-list-item
        prepend-icon="mdi-calculator-variant"
        title="AP Calculus Review"
        subtitle="Main Menu"
        class="pa-4"
      ></v-list-item>
      <v-divider></v-divider>
      <v-list density="compact" nav>
        <!-- Main Navigation Items -->
        <v-list-item
          v-for="item in mainNavItems"
          :key="item.to"
          :to="item.to"
          :title="item.title"
          :prepend-icon="item.icon"
          link
          active-class="text-primary font-weight-medium"
        ></v-list-item>
        
        <!-- Unit Guide Sections -->
        <!-- Limits Section -->
        <v-list-group value="limits">
          <template v-slot:activator="{ props }">
            <v-list-item
              v-bind="props"
              prepend-icon="mdi-chart-line"
              title="Limits"
            ></v-list-item>
          </template>
          
          <v-list-item
            v-for="unit in limitsUnits"
            :key="unit.to"
            :to="unit.to"
            :title="unit.title"
            link
            active-class="text-primary font-weight-medium"
            class="ml-4"
          ></v-list-item>
        </v-list-group>

        <!-- Derivatives Section -->
        <v-list-group value="derivatives">
          <template v-slot:activator="{ props }">
            <v-list-item
              v-bind="props"
              prepend-icon="mdi-chart-bell-curve-cumulative"
              title="Derivatives"
            ></v-list-item>
          </template>
          
          <v-list-item
            v-for="unit in derivativeUnits"
            :key="unit.to"
            :to="unit.to"
            :title="unit.title"
            link
            active-class="text-primary font-weight-medium"
            class="ml-4"
          ></v-list-item>
        </v-list-group>

        <!-- Integrals Section -->
        <v-list-group value="integrals">
          <template v-slot:activator="{ props }">
            <v-list-item
              v-bind="props"
              prepend-icon="mdi-chart-areaspline"
              title="Integrals"
            ></v-list-item>
          </template>
          
          <v-list-item
            v-for="unit in integralUnits"
            :key="unit.to"
            :to="unit.to"
            :title="unit.title"
            link
            active-class="text-primary font-weight-medium"
            class="ml-4"
          ></v-list-item>
        </v-list-group>
        
        <!-- Additional Navigation Items -->
        <v-list-item
          v-for="item in additionalNavItems"
          :key="item.to"
          :to="item.to"
          :title="item.title"
          :prepend-icon="item.icon"
          link
          active-class="text-primary font-weight-medium"
        ></v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app flat border="b" color="surface">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title class="font-weight-medium">AP Calculus Review</v-toolbar-title>
      <v-spacer></v-spacer>
      
      <SearchBar />
      </v-app-bar>

    <v-main class="bg-grey-lighten-4">
      <router-view />
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from 'vue';
import { useDisplay } from 'vuetify';
import SearchBar from '@/components/SearchBar.vue';

const { mobile } = useDisplay();
const drawer = ref(!mobile.value); // Open on desktop, closed on mobile by default

// Main navigation items (always visible)
const mainNavItems = [
  { title: 'Home', to: '/', icon: 'mdi-home-variant-outline' },
];

// Unit navigation items organized by topic
const limitsUnits = [
  { title: 'Unit 1: Limits & Continuity', to: '/units/limits'},
];

const derivativeUnits = [
  { title: 'Unit 2: Intro to Derivatives', to: '/units/differentiation-definition-properties'},
  { title: 'Unit 3: Derivative Techniques', to: '/units/differentiation-composite-implicit-inverse'},
  { title: 'Unit 4: Applications of Derivatives', to: '/units/contextual-applications-differentiation'},
  { title: 'Unit 5: Analyzing with Derivatives', to: '/units/analytical-applications-differentiation'},
];

const integralUnits = [
  { title: 'Unit 6: Intro to Integrals', to: '/units/integration-accumulation-change'},
  { title: 'Unit 7: Differential Equations', to: '/units/differential-equations'},
  { title: 'Unit 8: Applications of Integrals', to: '/units/applications-integration'},
];

// Additional navigation items (always visible)
const additionalNavItems = [
  { title: 'Practice Problems', to: '/practice', icon: 'mdi-pencil-outline' },
  { title: 'Formula Sheet', to: '/formula', icon: 'mdi-calculator' },
];
</script>

<style scoped>
/* Add any component-specific styles here if needed */
.v-main {
  /* Ensures v-main takes up available height if content is short, 
     adjust if you have a footer or other elements */
  min-height: calc(100vh - var(--v-layout-top)); /* var(--v-layout-top) is app-bar height */
}

/* You might want to style the active list item more distinctly if default is too subtle */
/* .v-list-item--active {
  background-color: rgba(var(--v-theme-primary-rgb), 0.1);
  border-left: 3px solid rgb(var(--v-theme-primary));
  font-weight: 600;
} */

.v-navigation-drawer .v-list-item-title {
  /* Ensure long titles don't break layout or wrap nicely */
  white-space: normal; /* Allow wrapping */
  line-height: 1.3;   /* Adjust line height for wrapped text */
}
</style>