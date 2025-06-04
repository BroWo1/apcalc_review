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

// Enhanced comprehensive searchable content with better keyword coverage and detailed descriptions
const searchableContent = [
  // Unit 1: Limits & Continuity - Enhanced Coverage
  {
    id: 'limits-definition-concept',
    title: 'Definition and Concept of Limits',
    parentUnit: 'Unit 1: Limits & Continuity',
    path: '/units/limits',
    keywords: ['limit', 'definition', 'approach', 'behavior', 'lim', 'x approaches c', 'one-sided', 'two-sided', 'left-hand', 'right-hand'],
    content: 'A limit describes what value a function f(x) approaches as x gets arbitrarily close to a specific point c. Written as lim[x→c] f(x) = L, it captures the function\'s behavior without requiring f(c) to exist. One-sided limits examine approach from left (x→c⁻) or right (x→c⁺).'
  },
  {
    id: 'limits-graphical-numerical',
    title: 'Finding Limits Graphically and Numerically',
    parentUnit: 'Unit 1: Limits & Continuity',
    path: '/units/limits',
    keywords: ['graphical limits', 'numerical limits', 'table of values', 'graph interpretation', 'estimate limit', 'visual analysis'],
    content: 'Estimate limits by examining function graphs and creating tables of values. Observe function behavior as x approaches the target value from both sides. Graphical analysis shows where functions are heading, while numerical tables provide approximate limit values.'
  },
  {
    id: 'limits-algebraic-techniques',
    title: 'Algebraic Techniques for Finding Limits',
    parentUnit: 'Unit 1: Limits & Continuity',
    path: '/units/limits',
    keywords: ['algebraic limits', 'direct substitution', 'factoring', 'rationalizing', 'limit laws', 'indeterminate forms', '0/0', 'simplification'],
    content: 'Algebraic methods for exact limit evaluation: direct substitution when possible, factoring to cancel common terms, rationalizing to eliminate radicals, and applying limit laws. Essential for resolving indeterminate forms like 0/0 that arise from direct substitution.'
  },
  {
    id: 'continuity-definition',
    title: 'Continuity: Definition and Conditions',
    parentUnit: 'Unit 1: Limits & Continuity',
    path: '/units/limits',
    keywords: ['continuity', 'continuous function', 'three conditions', 'f(c) exists', 'limit exists', 'limit equals function value', 'pencil test'],
    content: 'A function f is continuous at x=c if three conditions hold: (1) f(c) is defined, (2) lim[x→c] f(x) exists, and (3) lim[x→c] f(x) = f(c). Visually, continuous functions can be drawn without lifting your pencil. Continuity on intervals requires continuity at every point.'
  },
  {
    id: 'types-discontinuities',
    title: 'Types of Discontinuities',
    parentUnit: 'Unit 1: Limits & Continuity',
    path: '/units/limits',
    keywords: ['discontinuity', 'removable discontinuity', 'hole', 'jump discontinuity', 'infinite discontinuity', 'vertical asymptote', 'piecewise functions'],
    content: 'Three main types of discontinuities: (1) Removable (hole) - limit exists but doesn\'t equal function value, (2) Jump - left and right limits exist but are unequal, (3) Infinite - one or both one-sided limits approach ±∞, creating vertical asymptotes.'
  },
  {
    id: 'intermediate-value-theorem',
    title: 'Intermediate Value Theorem (IVT)',
    parentUnit: 'Unit 1: Limits & Continuity',
    path: '/units/limits',
    keywords: ['intermediate value theorem', 'IVT', 'continuous on closed interval', 'existence theorem', 'root finding', 'between values'],
    content: 'If f is continuous on [a,b] and N is between f(a) and f(b), then there exists c in (a,b) where f(c) = N. Guarantees that continuous functions take on all intermediate values. Useful for proving existence of solutions and roots.'
  },

  // Unit 2: Differentiation Definition & Properties - Enhanced
  {
    id: 'derivative-definition-limit',
    title: 'Definition of the Derivative',
    parentUnit: 'Unit 2: Differentiation: Definition and Fundamental Properties',
    path: '/units/differentiation-definition-properties',
    keywords: ['derivative', 'definition', 'limit definition', 'difference quotient', 'h approaches 0', 'instantaneous rate', 'slope of tangent', 'f prime'],
    content: 'The derivative f\'(a) = lim[h→0] (f(a+h) - f(a))/h measures instantaneous rate of change at x=a. This limit of the difference quotient gives the exact slope of the tangent line to the curve at point (a, f(a)).'
  },
  {
    id: 'geometric-interpretation',
    title: 'Geometric and Physical Interpretation',
    parentUnit: 'Unit 2: Differentiation: Definition and Fundamental Properties',
    path: '/units/differentiation-definition-properties',
    keywords: ['geometric interpretation', 'tangent line', 'slope', 'physical interpretation', 'velocity', 'position', 'rate of change', 'physics applications'],
    content: 'Geometrically, the derivative is the slope of the tangent line. Physically, if s(t) is position, then s\'(t) is velocity - the rate of change of position. The derivative concept extends to any rate of change: economics (marginal cost), biology (growth rates), etc.'
  },
  {
    id: 'differentiability-continuity',
    title: 'Differentiability and Continuity Relationship',
    parentUnit: 'Unit 2: Differentiation: Definition and Fundamental Properties',
    path: '/units/differentiation-definition-properties',
    keywords: ['differentiability', 'continuity', 'relationship', 'sharp corners', 'cusps', 'vertical tangents', 'absolute value function'],
    content: 'Differentiable functions must be continuous, but continuous functions aren\'t always differentiable. Non-differentiable points include sharp corners (like |x| at x=0), cusps, and vertical tangent lines where the derivative limit doesn\'t exist.'
  },
  {
    id: 'basic-differentiation-rules',
    title: 'Fundamental Differentiation Rules',
    parentUnit: 'Unit 2: Differentiation: Definition and Fundamental Properties',
    path: '/units/differentiation-definition-properties',
    keywords: ['power rule', 'constant rule', 'sum rule', 'difference rule', 'constant multiple rule', 'linearity', 'basic rules', 'd/dx'],
    content: 'Essential rules: Constant Rule d/dx[c] = 0, Power Rule d/dx[x^n] = nx^(n-1), Constant Multiple Rule d/dx[cf(x)] = c·f\'(x), Sum/Difference Rules d/dx[f±g] = f\'±g\'. These provide the foundation for all differentiation.'
  },
  {
    id: 'standard-derivatives',
    title: 'Common Derivatives and Higher Orders',
    parentUnit: 'Unit 2: Differentiation: Definition and Fundamental Properties',
    path: '/units/differentiation-definition-properties',
    keywords: ['trigonometric derivatives', 'sin cos tan', 'exponential derivatives', 'ex', 'logarithmic derivatives', 'ln x', 'second derivative', 'higher order derivatives', 'notation'],
    content: 'Standard derivatives: d/dx[sin x] = cos x, d/dx[cos x] = -sin x, d/dx[e^x] = e^x, d/dx[ln x] = 1/x. Higher-order derivatives like f\'\'(x) give information about concavity and acceleration. Various notations: f\'(x), dy/dx, d²y/dx².'
  },

  // Unit 3: Composite, Implicit & Inverse Functions - Enhanced
  {
    id: 'chain-rule-composite',
    title: 'The Chain Rule for Composite Functions',
    parentUnit: 'Unit 3: Differentiation: Composite, Implicit, and Inverse Functions',
    path: '/units/differentiation-composite-implicit-inverse',
    keywords: ['chain rule', 'composite functions', 'nested functions', 'outer function', 'inner function', 'f of g', 'function composition'],
    content: 'Chain Rule: d/dx[f(g(x))] = f\'(g(x)) · g\'(x). For composite functions where one function is inside another, multiply the derivative of the outer function (evaluated at the inner function) by the derivative of the inner function. Essential for complex function differentiation.'
  },
  {
    id: 'product-quotient-rules',
    title: 'Product and Quotient Rules',
    parentUnit: 'Unit 3: Differentiation: Composite, Implicit, and Inverse Functions',
    path: '/units/differentiation-composite-implicit-inverse',
    keywords: ['product rule', 'quotient rule', 'uv formula', 'low d-high minus high d-low', 'over low squared', 'multiplication', 'division'],
    content: 'Product Rule: d/dx[f·g] = f\'g + fg\' ("first times derivative of second plus second times derivative of first"). Quotient Rule: d/dx[f/g] = (f\'g - fg\')/g² ("low d-high minus high d-low, all over low squared").'
  },
  {
    id: 'implicit-differentiation-technique',
    title: 'Implicit Differentiation',
    parentUnit: 'Unit 3: Differentiation: Composite, Implicit, and Inverse Functions',
    path: '/units/differentiation-composite-implicit-inverse',
    keywords: ['implicit differentiation', 'dy/dx', 'implicit equations', 'related variables', 'chain rule application', 'solve for derivative'],
    content: 'Implicit differentiation finds dy/dx when x and y are related implicitly (like x² + y² = 25) rather than explicitly (y = f(x)). Differentiate both sides with respect to x, treating y as a function of x and applying the chain rule, then solve for dy/dx.'
  },
  {
    id: 'inverse-trig-derivatives',
    title: 'Derivatives of Inverse Functions',
    parentUnit: 'Unit 3: Differentiation: Composite, Implicit, and Inverse Functions',
    path: '/units/differentiation-composite-implicit-inverse',
    keywords: ['inverse functions', 'inverse trigonometric', 'arcsin', 'arccos', 'arctan', 'inverse derivatives', 'logarithmic differentiation'],
    content: 'Inverse trigonometric derivatives: d/dx[arcsin x] = 1/√(1-x²), d/dx[arccos x] = -1/√(1-x²), d/dx[arctan x] = 1/(1+x²). Logarithmic differentiation technique useful for products, quotients, and powers involving variables.'
  },

  // Unit 4: Contextual Applications - Enhanced
  {
    id: 'derivatives-rates-context',
    title: 'Derivatives as Rates of Change in Context',
    parentUnit: 'Unit 4: Contextual Applications of Differentiation',
    path: '/units/contextual-applications-differentiation',
    keywords: ['rate of change', 'instantaneous rate', 'average rate', 'units analysis', 'context problems', 'real world applications', 'interpretation'],
    content: 'Derivatives represent instantaneous rates of change in real contexts. Always include units: if f(t) has units of meters and t has units of seconds, then f\'(t) has units of meters/second. Compare with average rates: (f(b)-f(a))/(b-a).'
  },
  {
    id: 'motion-analysis-calculus',
    title: 'Motion Analysis: Position, Velocity, Acceleration',
    parentUnit: 'Unit 4: Contextual Applications of Differentiation',
    path: '/units/contextual-applications-differentiation',
    keywords: ['motion analysis', 'position', 'velocity', 'acceleration', 'displacement', 'distance traveled', 'particle motion', 's(t)', 'v(t)', 'a(t)'],
    content: 'Motion analysis using calculus: position s(t), velocity v(t) = s\'(t), acceleration a(t) = v\'(t) = s\'\'(t). Displacement is change in position; distance traveled requires integrating |v(t)|. Analyze when particle moves left/right, speeds up/slows down.'
  },
  {
    id: 'related-rates-strategy',
    title: 'Related Rates Problems and Strategy',
    parentUnit: 'Unit 4: Contextual Applications of Differentiation',
    path: '/units/contextual-applications-differentiation',
    keywords: ['related rates', 'changing quantities', 'problem solving strategy', 'implicit differentiation', 'chain rule', 'related variables', 'time derivatives'],
    content: 'Related rates solve problems where multiple quantities change with respect to time. Strategy: (1) Identify variables and what\'s given/asked, (2) Find equation relating variables, (3) Differentiate implicitly with respect to time, (4) Substitute known values and solve.'
  },
  {
    id: 'lhopital-rule-applications',
    title: 'L\'Hôpital\'s Rule and Linear Approximation',
    parentUnit: 'Unit 4: Contextual Applications of Differentiation',
    path: '/units/contextual-applications-differentiation',
    keywords: ['lhopital rule', 'indeterminate forms', '0/0', 'infinity/infinity', 'linearization', 'linear approximation', 'tangent line approximation', 'local linear'],
    content: 'L\'Hôpital\'s Rule: If lim f(x)/g(x) gives 0/0 or ∞/∞, then lim f(x)/g(x) = lim f\'(x)/g\'(x). Linear approximation uses tangent line L(x) = f(a) + f\'(a)(x-a) to estimate f(x) near x=a.'
  },

  // Unit 5: Analytical Applications - Enhanced
  {
    id: 'mean-value-theorem-applications',
    title: 'Mean Value Theorem and Applications',
    parentUnit: 'Unit 5: Analytical Applications of Differentiation',
    path: '/units/analytical-applications-differentiation',
    keywords: ['mean value theorem', 'MVT', 'average rate equals instantaneous rate', 'continuous', 'differentiable', 'existence theorem', 'Rolle theorem'],
    content: 'Mean Value Theorem: If f is continuous on [a,b] and differentiable on (a,b), then ∃c∈(a,b) where f\'(c) = (f(b)-f(a))/(b-a). Guarantees that some instantaneous rate equals the average rate. Foundation for many calculus theorems.'
  },
  {
    id: 'critical-points-extrema',
    title: 'Critical Points and Finding Extrema',
    parentUnit: 'Unit 5: Analytical Applications of Differentiation',
    path: '/units/analytical-applications-differentiation',
    keywords: ['critical points', 'extrema', 'maximum', 'minimum', 'f prime equals zero', 'undefined derivative', 'local extrema', 'global extrema'],
    content: 'Critical points occur where f\'(x) = 0 or f\'(x) is undefined. These are candidates for local extrema. Use First Derivative Test (sign changes of f\') or Second Derivative Test (f\'\'(c)) to classify critical points as maxima, minima, or neither.'
  },
  {
    id: 'first-second-derivative-tests',
    title: 'First and Second Derivative Tests',
    parentUnit: 'Unit 5: Analytical Applications of Differentiation',
    path: '/units/analytical-applications-differentiation',
    keywords: ['first derivative test', 'second derivative test', 'sign analysis', 'concavity test', 'classify extrema', 'max min test'],
    content: 'First Derivative Test: If f\' changes from + to - at c, then f(c) is local max; if - to +, then local min. Second Derivative Test: If f\'(c)=0 and f\'\'(c)>0, then local min; if f\'\'(c)<0, then local max; if f\'\'(c)=0, test is inconclusive.'
  },
  {
    id: 'function-behavior-analysis',
    title: 'Analyzing Function Behavior with Derivatives',
    parentUnit: 'Unit 5: Analytical Applications of Differentiation',
    path: '/units/analytical-applications-differentiation',
    keywords: ['increasing decreasing', 'concavity', 'concave up down', 'inflection points', 'function analysis', 'curve sketching', 'sign charts'],
    content: 'Function behavior from derivatives: f\'(x)>0 means increasing, f\'(x)<0 means decreasing. f\'\'(x)>0 means concave up (cup shape), f\'\'(x)<0 means concave down (cap shape). Inflection points where concavity changes (f\'\'(x)=0 and concavity changes).'
  },
  {
    id: 'optimization-applications',
    title: 'Optimization and Applied Problems',
    parentUnit: 'Unit 5: Analytical Applications of Differentiation',
    path: '/units/analytical-applications-differentiation',
    keywords: ['optimization', 'applied maximum minimum', 'constraint problems', 'objective function', 'feasible domain', 'word problems'],
    content: 'Optimization strategy: (1) Define variables and objective function to optimize, (2) Use constraints to express objective in terms of one variable, (3) Find domain restrictions, (4) Find critical points, (5) Test endpoints and critical points to find absolute extrema.'
  },

  // Unit 6: Integration & Accumulation - Enhanced
  {
    id: 'integration-concept-accumulation',
    title: 'Integration as Accumulation of Change',
    parentUnit: 'Unit 6: Integration and Accumulation of Change',
    path: '/units/integration-accumulation-change',
    keywords: ['integration', 'accumulation function', 'net change', 'total change', 'rate of change', 'area under curve', 'definite integral'],
    content: 'Integration accumulates change over intervals. If f(x) represents a rate of change, then ∫[a to b] f(x)dx gives the total accumulated change from x=a to x=b. Geometrically represents signed area under the curve f(x).'
  },
  {
    id: 'riemann-sums-approximation',
    title: 'Riemann Sums and Approximating Integrals',
    parentUnit: 'Unit 6: Integration and Accumulation of Change',
    path: '/units/integration-accumulation-change',
    keywords: ['riemann sums', 'left endpoint', 'right endpoint', 'midpoint rule', 'trapezoidal rule', 'delta x', 'approximation', 'partition'],
    content: 'Riemann sums approximate definite integrals using rectangles: Left/Right endpoint rules, Midpoint rule, Trapezoidal rule. As partition size approaches zero, the sum approaches the exact integral value: ∫[a to b] f(x)dx = lim[n→∞] Σf(xi*)Δx.'
  },
  {
    id: 'fundamental-theorem-calculus',
    title: 'The Fundamental Theorem of Calculus',
    parentUnit: 'Unit 6: Integration and Accumulation of Change',
    path: '/units/integration-accumulation-change',
    keywords: ['fundamental theorem', 'FTC', 'part 1', 'part 2', 'antiderivative', 'evaluation theorem', 'accumulation function', 'link differentiation integration'],
    content: 'Fundamental Theorem Part 1: d/dx ∫[a to x] f(t)dt = f(x) (derivative of accumulation function). Part 2: ∫[a to b] f(x)dx = F(b) - F(a) where F\'(x) = f(x) (evaluation theorem). Links differentiation and integration as inverse operations.'
  },
  {
    id: 'antiderivatives-indefinite',
    title: 'Antiderivatives and Indefinite Integrals',
    parentUnit: 'Unit 6: Integration and Accumulation of Change',
    path: '/units/integration-accumulation-change',
    keywords: ['antiderivatives', 'indefinite integral', 'constant of integration', '+C', 'reverse power rule', 'basic integrals', 'integration formulas'],
    content: 'Antiderivative F(x) satisfies F\'(x) = f(x). Indefinite integral ∫f(x)dx = F(x) + C includes arbitrary constant. Basic formulas: ∫x^n dx = x^(n+1)/(n+1) + C, ∫e^x dx = e^x + C, ∫1/x dx = ln|x| + C.'
  },
  {
    id: 'advanced-integration-techniques',
    title: 'Advanced Integration Techniques',
    parentUnit: 'Unit 6: Integration and Accumulation of Change',
    path: '/units/integration-accumulation-change',
    keywords: ['u-substitution', 'substitution method', 'integration by parts', 'partial fractions', 'trigonometric substitution', 'advanced techniques'],
    content: 'u-substitution: ∫f(g(x))g\'(x)dx = ∫f(u)du where u=g(x). Integration by parts: ∫u dv = uv - ∫v du (useful for products). Partial fractions decompose rational functions. Choose techniques based on function form.'
  },

  // Unit 7: Differential Equations - Enhanced
  {
    id: 'differential-equations-modeling',
    title: 'Modeling and Verifying Differential Equations',
    parentUnit: 'Unit 7: Differential Equations',
    path: '/units/differential-equations',
    keywords: ['differential equations', 'DE', 'modeling', 'verifying solutions', 'rate proportional', 'dy/dx', 'word problems', 'substitution'],
    content: 'Differential equations relate functions to derivatives: dy/dx = f(x,y). Model situations like "rate proportional to amount" → dy/dt = ky. Verify solutions by substituting into original equation. Set up DEs from word problems by identifying rates.'
  },
  {
    id: 'slope-fields-analysis',
    title: 'Slope Fields and Visual Analysis',
    parentUnit: 'Unit 7: Differential Equations',
    path: '/units/differential-equations',
    keywords: ['slope fields', 'direction fields', 'solution curves', 'equilibrium solutions', 'isoclines', 'visual analysis', 'sketching solutions'],
    content: 'Slope fields visualize dy/dx = f(x,y) by drawing short line segments with slopes f(x,y) at grid points. Sketch solution curves following the flow. Equilibrium solutions where dy/dx = 0 (horizontal tangents). Analyze long-term behavior.'
  },
  {
    id: 'eulers-method-numerical',
    title: 'Euler\'s Method for Numerical Solutions',
    parentUnit: 'Unit 7: Differential Equations',
    path: '/units/differential-equations',
    keywords: ['euler method', 'eulers method', 'numerical solution', 'approximation', 'step size', 'h', 'iteration', 'tangent line approximation'],
    content: 'Euler\'s Method: Starting at (x₀,y₀), use yn+1 = yn + h·f(xn,yn) where h is step size. Each step follows tangent line direction. Smaller h gives better accuracy but requires more steps. Essential when exact solutions are difficult.'
  },
  {
    id: 'separation-variables-solving',
    title: 'Solving by Separation of Variables',
    parentUnit: 'Unit 7: Differential Equations',
    path: '/units/differential-equations',
    keywords: ['separation of variables', 'separable', 'general solution', 'particular solution', 'initial conditions', 'integration both sides', 'constant of integration'],
    content: 'For separable equations dy/dx = g(x)h(y), rewrite as (1/h(y))dy = g(x)dx, then integrate both sides: ∫(1/h(y))dy = ∫g(x)dx. General solution contains arbitrary constant; use initial conditions to find particular solution.'
  },
  {
    id: 'exponential-logistic-models',
    title: 'Exponential and Logistic Growth Models',
    parentUnit: 'Unit 7: Differential Equations',
    path: '/units/differential-equations',
    keywords: ['exponential growth', 'exponential decay', 'logistic growth', 'carrying capacity', 'population models', 'radioactive decay', 'unlimited growth', 'limited growth'],
    content: 'Exponential model dy/dt = ky: unlimited growth (k>0) or decay (k<0), solution y = y₀e^(kt). Logistic model dP/dt = kP(1-P/L): limited growth approaching carrying capacity L, gives S-shaped curve. Models populations, epidemics, technology adoption.'
  },

  // Unit 8: Applications of Integration - Enhanced
  {
    id: 'average-value-applications',
    title: 'Average Value and Motion Applications',
    parentUnit: 'Unit 8: Applications of Integration',
    path: '/units/applications-integration',
    keywords: ['average value', 'mean value', 'f_avg', 'motion analysis', 'displacement', 'distance traveled', 'velocity', 'speed'],
    content: 'Average value: f_avg = (1/(b-a))∫[a,b]f(x)dx. Motion from velocity: displacement = ∫v(t)dt (net change in position), total distance = ∫|v(t)|dt. Distinguish between displacement (can be negative) and distance (always positive).'
  },
  {
    id: 'accumulation-functions',
    title: 'Accumulation Functions and Rate Analysis',
    parentUnit: 'Unit 8: Applications of Integration',
    path: '/units/applications-integration',
    keywords: ['accumulation functions', 'rate functions', 'total change', 'net change', 'F(x) = integral', 'rate of change applications'],
    content: 'If r(t) is a rate function, then ∫[a,b]r(t)dt gives total accumulation from t=a to t=b. Accumulation function F(x) = ∫[a,x]r(t)dt shows cumulative total up to time x. Apply FTC: F\'(x) = r(x).'
  },
  {
    id: 'area-between-curves-detailed',
    title: 'Area Between Curves',
    parentUnit: 'Unit 8: Applications of Integration',
    path: '/units/applications-integration',
    keywords: ['area between curves', 'top function minus bottom function', 'right minus left', 'intersection points', 'limits of integration', 'vertical strips', 'horizontal strips'],
    content: 'Area between f(x) and g(x): ∫[a,b]|f(x)-g(x)|dx. If f(x)≥g(x), use ∫[a,b](f(x)-g(x))dx. Find intersection points to determine limits. For functions of y, use ∫[c,d](right(y)-left(y))dy with horizontal strips.'
  },
  {
    id: 'volume-known-cross-sections',
    title: 'Volume by Cross-Sections',
    parentUnit: 'Unit 8: Applications of Integration',
    path: '/units/applications-integration',
    keywords: ['volume', 'cross sections', 'squares', 'equilateral triangles', 'semicircles', 'isosceles triangles', 'known cross sections', 'perpendicular'],
    content: 'Volume = ∫A(x)dx where A(x) is cross-sectional area perpendicular to x-axis. Common cross-sections: squares A=s², equilateral triangles A=(√3/4)s², semicircles A=(π/8)d², isosceles right triangles A=(1/2)s². Base region determines dimensions.'
  },
  {
    id: 'disc-method-revolution',
    title: 'Volume by Disc Method',
    parentUnit: 'Unit 8: Applications of Integration',
    path: '/units/applications-integration',
    keywords: ['disc method', 'disk method', 'solid of revolution', 'radius function', 'rotate around x-axis', 'rotate around y-axis', 'π r squared'],
    content: 'Disc method creates solid by rotating region around axis. Around x-axis: V = π∫[a,b][R(x)]²dx where R(x) is radius (distance from axis to curve). Around y-axis: V = π∫[c,d][R(y)]²dy. Each cross-section is a circular disc.'
  },
  {
    id: 'washer-method-hollow',
    title: 'Volume by Washer Method',
    parentUnit: 'Unit 8: Applications of Integration',
    path: '/units/applications-integration',
    keywords: ['washer method', 'outer radius', 'inner radius', 'hollow solid', 'doughnut', 'rotation', 'bounded by two curves'],
    content: 'Washer method for hollow solids: V = π∫[a,b]([R(x)]² - [r(x)]²)dx where R(x) is outer radius, r(x) is inner radius. Region bounded by two curves creates washer-shaped cross-sections when rotated. Like disc method with hole removed.'
  },
  {
    id: 'arc-length-parametric',
    title: 'Arc Length and Parametric Curves',
    parentUnit: 'Unit 8: Applications of Integration',
    path: '/units/applications-integration',
    keywords: ['arc length', 'curve length', 'parametric curves', 'distance formula', 'dx/dt', 'dy/dt', 'speed'],
    content: 'Arc length for y=f(x): L = ∫[a,b]√(1+[f\'(x)]²)dx. For parametric curves (x(t),y(t)): L = ∫[t1,t2]√([dx/dt]²+[dy/dt]²)dt. This integrates the speed along the curve. Represents total distance traveled along the path.'
  }
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
