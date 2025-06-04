<template>
  <v-menu
    v-model="menuOpen"
    offset-y
    :close-on-content-click="false"
    location="bottom end"
    max-height="400px"
  >
    <template v-slot:activator="{ props: menuProps }">
      <v-text-field
        v-bind="{ ...menuProps, ...textFieldProps }"
        v-model="searchQuery"
        density="compact"
        single-line
        hide-details
        @input="performSearch"
        @click:append-inner="performSearch"
        @keydown.enter="performSearch"
        :class="props.class"
        :style="textFieldStyle"
      ></v-text-field>
    </template>

    <v-list v-if="results.length">
      <v-list-item
        v-for="(result, index) in results"
        :key="index"
        :to="result.path"
        @click="handleResultClick(result)"
      >
        <v-list-item-title v-html="highlightMatch(result.title)"></v-list-item-title>
        <v-list-item-subtitle>{{ result.parentUnit }}</v-list-item-subtitle>
      </v-list-item>
    </v-list>
    <v-card v-else-if="searchQuery && !results.length && menuOpen" class="pa-3 text-center"> <v-card-text>No results found for "{{ searchQuery }}".</v-card-text>
    </v-card>
  </v-menu>
</template>

<script setup>
import { ref, nextTick, computed } from 'vue';
import { useRouter } from 'vue-router';

// Define props for customization
const props = defineProps({
  variant: {
    type: String,
    default: 'solo'
  },
  rounded: {
    type: [Boolean, String],
    default: false
  },
  flat: {
    type: Boolean,
    default: false
  },
  label: {
    type: String,
    default: 'Search concepts...'
  },
  maxWidth: {
    type: String,
    default: '350px'
  },
  class: {
    type: String,
    default: 'mx-2'
  },
  prependInnerIcon: {
    type: String,
    default: 'mdi-magnify'
  }
});

const searchQuery = ref('');
const results = ref([]);
const menuOpen = ref(false);
const router = useRouter();

// Computed styles
const textFieldProps = computed(() => ({
  variant: props.variant,
  rounded: props.rounded ? 'lg' : false,
  flat: props.flat,
  label: props.label,
  'prepend-inner-icon': props.prependInnerIcon,
  'append-inner-icon': props.variant === 'solo' ? 'mdi-magnify' : undefined
}));

const textFieldStyle = computed(() => ({
  'max-width': props.maxWidth
}));

const searchableContent = [
  // Unit 1: Limits & Continuity
  {
    id: 'limits-intro',
    title: 'Understanding the concept of a limit',
    parentUnit: 'Unit 1: Limits & Continuity',
    path: '/units/limits',
    keywords: ['limit', 'concept', 'definition', 'approach', 'limit definition'],
    content: 'The limit of a function f(x) as x approaches c is a value L that f(x) gets closer to as x gets closer to c. It describes the behavior of a function near a particular point.'
  },
  {
    id: 'limits-algebraic',
    title: 'Calculating limits using algebraic techniques',
    parentUnit: 'Unit 1: Limits & Continuity',
    path: '/units/limits',
    keywords: ['limit', 'algebraic', 'techniques', 'factoring', 'rationalizing', 'solving limits'],
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

  // Unit 2: Differentiation: Definition and Fundamental Properties
  {
    id: 'derivative-def',
    title: 'Definition of the derivative',
    parentUnit: 'Unit 2: Differentiation: Definition and Fundamental Properties',
    path: '/units/differentiation-definition-properties',
    keywords: ['derivative', 'definition', 'slope', 'tangent line', 'rate of change', 'derivative definition'],
    content: 'The derivative of a function f(x) at a point x, denoted f\'(x), is the instantaneous rate of change of the function, or the slope of the tangent line to the graph of the function at that point. It is defined as the limit of the difference quotient: $$\lim_{h \\to 0} \\frac{f(x+h) - f(x)}{h}$$.'
  },
  {
    id: 'differentiation-rules',
    title: 'Power rule, product rule, quotient rule',
    parentUnit: 'Unit 2: Differentiation: Definition and Fundamental Properties',
    path: '/units/differentiation-definition-properties',
    keywords: ['power rule', 'product rule', 'quotient rule', 'differentiation rules', 'fundamental properties'],
    content: 'The power rule states that $$\\frac{d}{dx}(x^n) = nx^{n-1}$$. The product rule is used for the derivative of a product of two functions. The quotient rule is for the derivative of a quotient of two functions.'
  },

  // Unit 3: Differentiation: Composite, Implicit, and Inverse Functions
  {
    id: 'chain-rule',
    title: 'Chain rule for composite functions',
    parentUnit: 'Unit 3: Differentiation: Composite, Implicit, and Inverse Functions',
    path: '/units/differentiation-composite-implicit-inverse',
    keywords: ['chain rule', 'composite functions', 'derivative of composition'],
    content: 'The chain rule states that if y = f(g(x)), then dy/dx = f\'(g(x)) · g\'(x). This rule is essential for differentiating composite functions.'
  },
  {
    id: 'implicit-differentiation',
    title: 'Implicit differentiation techniques',
    parentUnit: 'Unit 3: Differentiation: Composite, Implicit, and Inverse Functions',
    path: '/units/differentiation-composite-implicit-inverse',
    keywords: ['implicit differentiation', 'implicit', 'related variables'],
    content: 'Implicit differentiation is used when y is not explicitly solved for in terms of x. We differentiate both sides of an equation with respect to x, treating y as a function of x.'
  },
  {
    id: 'inverse-functions',
    title: 'Derivatives of inverse functions',
    parentUnit: 'Unit 3: Differentiation: Composite, Implicit, and Inverse Functions',
    path: '/units/differentiation-composite-implicit-inverse',
    keywords: ['inverse functions', 'inverse', 'derivative of inverse'],
    content: 'For inverse functions, if y = f(x) and x = f⁻¹(y), then the derivative of the inverse function is given by (f⁻¹)\'(y) = 1/f\'(x).'
  },

  // Unit 4: Contextual Applications of Differentiation
  {
    id: 'related-rates',
    title: 'Related rates problems',
    parentUnit: 'Unit 4: Contextual Applications of Differentiation',
    path: '/units/contextual-applications-differentiation',
    keywords: ['related rates', 'rate of change', 'applications'],
    content: 'Related rates problems involve finding the rate of change of one quantity given the rate of change of a related quantity. These problems often involve geometric relationships and real-world scenarios.'
  },
  {
    id: 'lhopitals-rule',
    title: "L'Hôpital's rule for indeterminate forms",
    parentUnit: 'Unit 4: Contextual Applications of Differentiation',
    path: '/units/contextual-applications-differentiation',
    keywords: ["l'hopital's rule", "lhopital", "indeterminate forms", "0/0", "∞/∞"],
    content: "L'Hôpital's rule states that if lim f(x)/g(x) results in 0/0 or ∞/∞, then lim f(x)/g(x) = lim f'(x)/g'(x), provided the latter limit exists."
  },
  {
    id: 'optimization-contextual',
    title: 'Optimization in real-world contexts',
    parentUnit: 'Unit 4: Contextual Applications of Differentiation',
    path: '/units/contextual-applications-differentiation',
    keywords: ['optimization', 'maximum', 'minimum', 'real-world', 'applications'],
    content: 'Optimization problems involve finding maximum or minimum values of functions in real-world contexts, such as minimizing cost or maximizing profit.'
  },

  // Unit 5: Analytical Applications of Differentiation
  {
    id: 'curve-sketching',
    title: 'Curve sketching and function analysis',
    parentUnit: 'Unit 5: Analytical Applications of Differentiation',
    path: '/units/analytical-applications-differentiation',
    keywords: ['curve sketching', 'function analysis', 'concavity', 'inflection points'],
    content: 'Curve sketching involves analyzing the behavior of functions using derivatives to determine intervals of increase/decrease, concavity, and critical points.'
  },
  {
    id: 'mean-value-theorem',
    title: 'Mean Value Theorem and its applications',
    parentUnit: 'Unit 5: Analytical Applications of Differentiation',
    path: '/units/analytical-applications-differentiation',
    keywords: ['mean value theorem', 'MVT', 'rolle\'s theorem'],
    content: 'The Mean Value Theorem states that if f is continuous on [a,b] and differentiable on (a,b), then there exists c in (a,b) such that f\'(c) = (f(b)-f(a))/(b-a).'
  },
  {
    id: 'optimization-problems',
    title: 'Advanced optimization problems',
    parentUnit: 'Unit 5: Analytical Applications of Differentiation',
    path: '/units/analytical-applications-differentiation',
    keywords: ['optimization problems', 'critical points', 'extrema', 'maximum', 'minimum'],
    content: 'Advanced optimization involves using calculus to find absolute and relative extrema, analyzing critical points, and solving complex optimization scenarios.'
  },

  // Unit 6: Integration and Accumulation of Change
  {
    id: 'definite-integrals',
    title: 'Definite integrals and Riemann sums',
    parentUnit: 'Unit 6: Integration and Accumulation of Change',
    path: '/units/integration-accumulation-change',
    keywords: ['definite integrals', 'riemann sums', 'area under curve'],
    content: 'A definite integral represents the signed area under a curve and is the limit of Riemann sums as the number of subdivisions approaches infinity.'
  },
  {
    id: 'fundamental-theorem',
    title: 'Fundamental Theorem of Calculus',
    parentUnit: 'Unit 6: Integration and Accumulation of Change',
    path: '/units/integration-accumulation-change',
    keywords: ['fundamental theorem', 'FTC', 'antiderivative', 'integration'],
    content: 'The Fundamental Theorem of Calculus connects differentiation and integration, stating that integration and differentiation are inverse operations.'
  },
  {
    id: 'integration-techniques',
    title: 'Basic integration techniques',
    parentUnit: 'Unit 6: Integration and Accumulation of Change',
    path: '/units/integration-accumulation-change',
    keywords: ['integration techniques', 'substitution', 'integration by parts', 'antiderivatives'],
    content: 'Integration techniques include basic antiderivatives, u-substitution, and integration by parts for finding indefinite and definite integrals.'
  },

  // Unit 7: Differential Equations
  {
    id: 'solving-des',
    title: 'Solving differential equations',
    parentUnit: 'Unit 7: Differential Equations',
    path: '/units/differential-equations',
    keywords: ['solving differential equations', 'separable', 'first order', 'solving des'],
    content: 'Differential equations involve functions and their derivatives. Common methods include separation of variables for first-order equations.'
  },
  {
    id: 'slope-fields',
    title: 'Slope fields and solution curves',
    parentUnit: 'Unit 7: Differential Equations',
    path: '/units/differential-equations',
    keywords: ['slope fields', 'direction fields', 'solution curves'],
    content: 'Slope fields (direction fields) are graphical representations of differential equations that show the slope of solution curves at various points.'
  },
  {
    id: 'exponential-growth-decay',
    title: 'Exponential growth and decay models',
    parentUnit: 'Unit 7: Differential Equations',
    path: '/units/differential-equations',
    keywords: ['exponential growth', 'exponential decay', 'growth models', 'decay models'],
    content: 'Exponential growth and decay are modeled by differential equations of the form dy/dt = ky, leading to solutions of the form y = Ae^(kt).'
  },

  // Unit 8: Applications of Integration
  {
    id: 'area-between-curves',
    title: 'Area between curves',
    parentUnit: 'Unit 8: Applications of Integration',
    path: '/units/applications-integration',
    keywords: ['area between curves', 'region area', 'integration applications'],
    content: 'The area between two curves f(x) and g(x) from x=a to x=b is given by the integral of |f(x) - g(x)| over the interval [a,b].'
  },
  {
    id: 'volumes-of-solids',
    title: 'Volumes of solids of revolution',
    parentUnit: 'Unit 8: Applications of Integration',
    path: '/units/applications-integration',
    keywords: ['volumes of solids', 'solids of revolution', 'disk method', 'washer method'],
    content: 'Volumes of solids formed by rotating regions around axes can be calculated using disk/washer methods or cylindrical shells method.'
  },
  {
    id: 'net-change',
    title: 'Net change and accumulation',
    parentUnit: 'Unit 8: Applications of Integration',
    path: '/units/applications-integration',
    keywords: ['net change', 'accumulation', 'total change', 'integration applications'],
    content: 'The net change in a quantity over an interval is given by the definite integral of its rate of change over that interval.'
  }
];

const performSearch = () => {
  console.log('[SEARCH] performSearch triggered. Query:', searchQuery.value);

  if (!searchQuery.value || searchQuery.value.trim() === '') {
    results.value = [];
    menuOpen.value = false;
    console.log('[SEARCH] Query empty or just spaces. Results cleared. Menu open:', menuOpen.value);
    return;
  }

  const lowerCaseQuery = searchQuery.value.trim().toLowerCase();
  results.value = searchableContent.filter(item => {
    const titleMatch = item.title.toLowerCase().includes(lowerCaseQuery);
    const contentMatch = item.content.toLowerCase().includes(lowerCaseQuery);
    const keywordMatch = item.keywords.some(keyword => keyword.toLowerCase().includes(lowerCaseQuery));
    return titleMatch || contentMatch || keywordMatch;
  });

  // Crucial logic for opening the menu
  menuOpen.value = results.value.length > 0 || (searchQuery.value.trim() !== '');
  
  console.log(`[SEARCH] Query: "${lowerCaseQuery}". Results found: ${results.value.length}. Menu open: ${menuOpen.value}`);

  if (menuOpen.value && results.value.length === 0 && searchQuery.value.trim() !== '') {
    console.log('[SEARCH] Displaying "No results found" message.');
  }


  // Re-render MathJax if present in search results (check content too, if highlighted)
  // This is less likely to be the cause of results *not showing* at all.
  if (window.MathJax && results.value.some(r => r.title.includes('$') || r.content.includes('$'))) {
    nextTick(() => {
      if (window.MathJax.typesetPromise) {
         window.MathJax.typesetPromise();
      } else if (window.MathJax.Hub && window.MathJax.Hub.Queue) { // For older MathJax
         window.MathJax.Hub.Queue(["Typeset", window.MathJax.Hub]);
      }
    }).catch(error => console.error("MathJax typesetting error:", error));
  }
};

const highlightMatch = (text) => {
  if (!searchQuery.value || !text) return text;
  const query = searchQuery.value.trim();
  if (!query) return text; // Avoid empty regex
  try {
    const regex = new RegExp(`(${query.replace(/[.*+?^${}()|[\]\\]/g, '\\$&')})`, 'gi');
    return text.replace(regex, '<mark class="search-highlight">$1</mark>');
  } catch (e) {
    console.error("Error creating regex for highlighting:", e);
    return text; // Return original text if regex fails
  }
};

const handleResultClick = (result) => {
  console.log('[SEARCH] Result clicked:', result.title, 'Navigating to:', result.path);
  if (result.path) { // Ensure path exists
    router.push(result.path);
  }
  searchQuery.value = ''; 
  results.value = [];
  menuOpen.value = false;
};

</script>

<style scoped>
/* Using :deep selector or global style if <mark> is not directly in this component's template scope after v-html */
:deep(mark.search-highlight),
mark { /* Fallback for direct mark styling */
  background-color: yellow;
  font-weight: bold;
  color: black; /* Ensure text is visible on yellow */
}
.v-list-item {
  cursor: pointer;
}
</style>