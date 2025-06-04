<template>
  <v-container>
    <h1 class="text-h4 mb-4">Search Results for "{{ searchQuery }}"</h1>
    <v-row v-if="results.length">
      <v-col v-for="(result, index) in results" :key="index" cols="12">
        <v-card :to="result.path">
          <v-card-title>{{ result.title }}</v-card-title>
          <v-card-subtitle>{{ result.parentUnit }}</v-card-subtitle>
          <v-card-text>
            <p v-html="highlightMatch(result.contentSnippet)"></p>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row v-else>
      <v-col cols="12">
        <p class="text-body-1">No results found for "{{ searchQuery }}".</p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref, computed, onMounted, watch } from 'vue';
import { useRoute } from 'vue-router';

const route = useRoute();
const searchQuery = ref(route.query.q || '');
const results = ref([]);

// Define searchable content here. 
// This is a simplified example. In a real app, you might fetch this from a store or API,
// or dynamically import content from your unit pages.
const searchableContent = [
  {
    id: 'limits-intro',
    title: 'Understanding the concept of a limit',
    parentUnit: 'Unit 1: Limits & Continuity',
    path: '/units/limits',
    keywords: ['limit', 'concept', 'definition', 'approach'],
    content: 'The limit of a function f(x) as x approaches c is a value L that f(x) gets closer to as x gets closer to c. It describes the behavior of a function near a particular point.'
  },
  {
    id: 'limits-algebraic',
    title: 'Calculating limits using algebraic techniques',
    parentUnit: 'Unit 1: Limits & Continuity',
    path: '/units/limits',
    keywords: ['limit', 'algebraic', 'techniques', 'factoring', 'rationalizing'],
    content: 'Algebraic techniques for finding limits include direct substitution, factoring, rationalizing the numerator or denominator, and using limit laws. For example, the limit of x^2 as x approaches 2 is 4.'
  },
  {
    id: 'continuity-def',
    title: 'Continuity and its properties',
    parentUnit: 'Unit 1: Limits & Continuity',
    path: '/units/limits',
    keywords: ['continuity', 'continuous', 'properties', 'removable discontinuity', 'jump discontinuity'],
    content: 'A function is continuous at a point c if the limit of f(x) as x approaches c exists, f(c) is defined, and the limit equals f(c). Properties include sums, differences, products, and quotients of continuous functions also being continuous.'
  },
  {
    id: 'derivative-def',
    title: 'Definition of the derivative',
    parentUnit: 'Unit 2: Differentiation: Definition and Fundamental Properties',
    path: '/units/differentiation-definition-properties',
    keywords: ['derivative', 'definition', 'slope', 'tangent line', 'rate of change'],
    content: 'The derivative of a function f(x) at a point x, denoted second derivative is the instantaneous rate of change of the function, or the slope of the tangent line to the graph of the function at that point. It is defined as the limit of the difference quotient: $$\\lim_{h \\to 0} \\frac{f(x+h) - f(x)}{h}$$.'
  },
  {
    id: 'power-rule',
    title: 'Power rule, product rule, quotient rule',
    parentUnit: 'Unit 2: Differentiation: Definition and Fundamental Properties',
    path: '/units/differentiation-definition-properties',
    keywords: ['power rule', 'product rule', 'quotient rule', 'differentiation rules'],
    content: 'The power rule states that $$\\frac{d}{dx}(x^n) = nx^{n-1}$$. The product rule is used for the derivative of a product of two functions. The quotient rule is for the derivative of a quotient of two functions.'
  },
  // Unit 3
  {
    id: 'chain-rule',
    title: 'Chain Rule',
    parentUnit: 'Unit 3: Differentiation: Composite, Implicit, and Inverse Functions',
    path: '/units/differentiation-composite-implicit-inverse',
    keywords: ['chain rule', 'composite functions', 'differentiation'],
    content: 'The chain rule is a formula to compute the derivative of a composite function. If f and g are functions, then the chain rule expresses the derivative of their composition f(g(x)) in terms of the derivatives of f and g.'
  },
  {
    id: 'implicit-differentiation',
    title: 'Implicit Differentiation',
    parentUnit: 'Unit 3: Differentiation: Composite, Implicit, and Inverse Functions',
    path: '/units/differentiation-composite-implicit-inverse',
    keywords: ['implicit differentiation', 'implicit functions', 'derivatives'],
    content: 'Implicit differentiation is a technique used to find the derivative of implicitly defined functions, where it is difficult or impossible to solve for one variable in terms of the other.'
  },
  // Unit 4
  {
    id: 'related-rates',
    title: 'Related Rates',
    parentUnit: 'Unit 4: Contextual Applications of Differentiation',
    path: '/units/contextual-applications-differentiation',
    keywords: ['related rates', 'differentiation applications', 'problem solving'],
    content: 'Related rates problems involve finding a rate at which a quantity changes by relating that quantity to other quantities whose rates of change are known.'
  },
  {
    id: 'lhopitals-rule',
    title: 'L\'Hôpital\'s Rule',
    parentUnit: 'Unit 4: Contextual Applications of Differentiation',
    path: '/units/contextual-applications-differentiation',
    keywords: ['lhopital\'s rule', 'limits', 'indeterminate forms'],
    content: 'L\'Hôpital\'s Rule is used to evaluate limits of indeterminate forms such as 0/0 or ∞/∞ by taking derivatives of the numerator and denominator.'
  },
  // Unit 5
  {
    id: 'curve-sketching',
    title: 'Curve Sketching',
    parentUnit: 'Unit 5: Analytical Applications of Differentiation',
    path: '/units/analytical-applications-differentiation',
    keywords: ['curve sketching', 'derivatives', 'graphing functions', 'maxima', 'minima', 'concavity'],
    content: 'Curve sketching involves using derivatives to find critical points, intervals of increase/decrease, concavity, and inflection points to accurately graph a function.'
  },
  {
    id: 'optimization-problems',
    title: 'Optimization Problems',
    parentUnit: 'Unit 5: Analytical Applications of Differentiation',
    path: '/units/analytical-applications-differentiation',
    keywords: ['optimization', 'calculus', 'maxima', 'minima', 'applied problems'],
    content: 'Optimization problems involve finding the maximum or minimum value of a quantity subject to certain constraints, often solved using derivatives.'
  },
  // Unit 6
  {
    id: 'definite-integrals',
    title: 'Definite Integrals and the Fundamental Theorem of Calculus',
    parentUnit: 'Unit 6: Integration and Accumulation of Change',
    path: '/units/integration-accumulation-change',
    keywords: ['definite integral', 'fundamental theorem of calculus', 'integration', 'area under curve'],
    content: 'The definite integral represents the accumulated change or area under a curve. The Fundamental Theorem of Calculus connects differentiation and integration.'
  },
  {
    id: 'integration-techniques',
    title: 'Integration Techniques',
    parentUnit: 'Unit 6: Integration and Accumulation of Change',
    path: '/units/integration-accumulation-change',
    keywords: ['integration techniques', 'u-substitution', 'integration by parts'],
    content: 'Various techniques are used to find antiderivatives (integrals), such as u-substitution, integration by parts, and trigonometric substitution.'
  },
  // Unit 7
  {
    id: 'solving-des',
    title: 'Solving Differential Equations',
    parentUnit: 'Unit 7: Differential Equations',
    path: '/units/differential-equations',
    keywords: ['differential equations', 'solving DEs', 'separation of variables', 'slope fields'],
    content: 'Differential equations relate a function with its derivatives. Techniques for solving them include separation of variables and using slope fields to visualize solutions.'
  },
  {
    id: 'exponential-growth-decay',
    title: 'Exponential Growth and Decay',
    parentUnit: 'Unit 7: Differential Equations',
    path: '/units/differential-equations',
    keywords: ['exponential growth', 'exponential decay', 'differential equations applications'],
    content: 'Many real-world phenomena, such as population growth or radioactive decay, can be modeled using differential equations that lead to exponential growth or decay functions.'
  },
  // Unit 8
  {
    id: 'area-between-curves',
    title: 'Area Between Curves',
    parentUnit: 'Unit 8: Applications of Integration',
    path: '/units/applications-integration',
    keywords: ['area between curves', 'integration applications', 'definite integrals'],
    content: 'The area between two curves can be found by integrating the difference of the functions over a specified interval.'
  },
  {
    id: 'volumes-solids',
    title: 'Volumes of Solids',
    parentUnit: 'Unit 8: Applications of Integration',
    path: '/units/applications-integration',
    keywords: ['volumes of solids', 'disk method', 'washer method', 'shell method', 'integration applications'],
    content: 'Integration can be used to find the volumes of solids of revolution (using disk, washer, or shell methods) or solids with known cross-sections.'
  }
  // Add more searchable items for each concept/formula
];

const performSearch = (query) => {
  if (!query || query.trim() === '') {
    results.value = [];
    return;
  }
  const lowerCaseQuery = query.trim().toLowerCase();
  results.value = searchableContent.filter(item => {
    return (
      item.title.toLowerCase().includes(lowerCaseQuery) ||
      item.content.toLowerCase().includes(lowerCaseQuery) ||
      item.keywords.some(keyword => keyword.toLowerCase().includes(lowerCaseQuery))
    );
  }).map(item => ({
    ...item,
    contentSnippet: item.content.substring(0, 150) + (item.content.length > 150 ? '...' : '') // Create a snippet
  }));

  // Re-render MathJax if present in search results
  if (window.MathJax && results.value.some(r => r.content.includes('$'))) {
    nextTick(() => {
      window.MathJax.typesetPromise();
    });
  }
};

const highlightMatch = (text) => {
  if (!searchQuery.value || !text) return text;
  const regex = new RegExp(`(${searchQuery.value.replace(/[.*+?^${}()|[\]\\]/g, '\\$&')})`, 'gi');
  return text.replace(regex, '<mark>$1</mark>');
};

watch(() => route.query.q, (newQuery) => {
  searchQuery.value = newQuery || '';
  performSearch(newQuery);
});

onMounted(() => {
  performSearch(searchQuery.value);
});

</script>

<style scoped>
mark {
  background-color: yellow;
  font-weight: bold;
}
</style>
