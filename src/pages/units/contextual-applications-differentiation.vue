<template>
  <v-container class="pa-0 bg-grey-lighten-4" style="min-height: 100vh;" fluid>
    <v-row justify="center" align="start" style="min-height: inherit;" class="py-md-6">
      <v-col cols="12" md="11" lg="9" xl="8">
        <v-card elevation="4" rounded="xl" class="pa-5 pa-md-8">
          <v-card-title class="text-h4 font-weight-bold mb-2 text-primary">Unit 4: Contextual Applications of Differentiation</v-card-title>
          <v-card-text>
            <p class="text-body-1 mb-4">
              This unit transitions from the mechanics of differentiation (covered in <strong>Unit 2</strong> and <strong>Unit 3</strong>) to its powerful applications in real-world contexts. You will learn to interpret derivatives as rates of change in various scenarios, analyze motion, solve problems involving related rates, approximate function values using linearization, and evaluate limits of indeterminate forms using L'Hopital's Rule. These tools allow for a deeper understanding of how functions model dynamic situations and provide quantitative insights into changing systems.
            </p>

            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="indigo-darken-2" class="mr-3 mt-1">mdi-chart-timeline-variant</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Derivatives as Rates of Change</h2>
                  <div class="text-body-1">
                    The derivative $f'(a)$ represents the <strong>instantaneous rate of change</strong> of $f$ with respect to $x$ at point $a$. The units are always (units of $f$)/(units of $x$).
                    <br><br>
                    <strong>Common Applications:</strong>
                    <ul class="pl-4 mt-1">
                      <li><strong>Economics:</strong> Marginal cost $C'(x)$, marginal revenue, marginal profit</li>
                      <li><strong>Population:</strong> Growth rate $P'(t)$ (people per year)</li>
                      <li><strong>Chemistry:</strong> Reaction rates (concentration change over time)</li>
                      <li><strong>Physics:</strong> Cooling/heating rates, radioactive decay rates</li>
                      <li><strong>Environmental:</strong> Pollutant concentration changes</li>
                    </ul>
                    Understanding context is crucial for meaningful interpretation of derivatives.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="deep-orange-darken-2" class="mr-3 mt-1">mdi-run-fast</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Motion Analysis</h2>
                  <div class="text-body-1">
                    For an object moving along a straight line with position function $s(t)$:
                    <ul class="pl-4 mt-1">
                      <li><strong>Position:</strong> $s(t)$ (location at time $t$)</li>
                      <li><strong>Velocity:</strong> $v(t) = s'(t)$ (rate and direction of motion)</li>
                      <li><strong>Acceleration:</strong> $a(t) = v'(t) = s''(t)$ (rate of velocity change)</li>
                      <li><strong>Speed:</strong> $|v(t)|$ (magnitude of velocity)</li>
                    </ul>
                    <br>
                    <strong>Motion Analysis:</strong>
                    <ul class="pl-4 mt-1">
                      <li>Speeding up: $v(t)$ and $a(t)$ have same sign</li>
                      <li>Slowing down: $v(t)$ and $a(t)$ have opposite signs</li>
                      <li>At rest: $v(t) = 0$</li>
                      <li>Changing direction: $v(t)$ changes sign</li>
                    </ul>
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="green-darken-3" class="mr-3 mt-1">mdi-link-variant-plus</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Related Rates Problems</h2>
                  <div class="text-body-1">
                    When multiple quantities change with time and are related by an equation, we can find unknown rates using known rates and implicit differentiation.
                    <br><br>
                    <strong>Solution Strategy:</strong>
                    <ol class="pl-4 mt-1">
                      <li><strong>Understand:</strong> Identify changing quantities and draw a diagram</li>
                      <li><strong>Variables & Rates:</strong> List known rates (e.g., $\frac{dx}{dt}$) and desired rate</li>
                      <li><strong>Equation:</strong> Find relationship between variables (geometry, physics, etc.)</li>
                      <li><strong>Differentiate:</strong> Take $\frac{d}{dt}$ of both sides using Chain Rule</li>
                      <li><strong>Substitute & Solve:</strong> Plug in known values and solve for desired rate</li>
                      <li><strong>Check:</strong> Verify units and reasonableness</li>
                    </ol>
                    <br>
                    <strong>Example:</strong> If sphere radius changes at rate $\frac{dr}{dt}$, then volume changes at rate $\frac{dV}{dt} = 4\pi r^2 \frac{dr}{dt}$ (from $V = \frac{4}{3}\pi r^3$).
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="amber-darken-3" class="mr-3 mt-1">mdi-chart-line</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Linear Approximation and L'Hôpital's Rule</h2>
                  <div class="text-body-1">
                    <strong>Linearization (Tangent Line Approximation):</strong>
                    The tangent line at $(a, f(a))$ provides a linear approximation:
                    $$L(x) = f(a) + f'(a)(x-a)$$
                    For $x$ near $a$: $f(x) \approx L(x)$. Used to approximate function values and estimate changes.
                    <br><br>
                    <strong>L'Hôpital's Rule:</strong>
                    For indeterminate forms $\frac{0}{0}$ or $\frac{\infty}{\infty}$:
                    $$\lim_{x \to c} \frac{f(x)}{g(x)} = \lim_{x \to c} \frac{f'(x)}{g'(x)}$$
                    (provided the limit on the right exists)
                    <br><br>
                    <strong>Key Points:</strong>
                    <ul class="pl-4 mt-1">
                      <li>Always verify indeterminate form before applying</li>
                      <li>Can be applied repeatedly if needed</li>
                      <li>Other forms ($0 \cdot \infty$, $\infty - \infty$, $1^\infty$, $0^0$, $\infty^0$) require algebraic manipulation first</li>
                    </ul>
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <h2 class="text-h5 font-weight-medium mb-3">Key Formulas & Concepts 📝</h2>
              <v-row>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">Rate Interpretation:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>$f'(a)$ = instantaneous rate of change at $x=a$</li>
                    <li>Units: (units of $f$)/(units of $x$)</li>
                  </ul>

                  <h3 class="text-h6 mb-2 mt-3">Motion Analysis:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>Velocity: $v(t) = s'(t)$</li>
                    <li>Acceleration: $a(t) = v'(t) = s''(t)$</li>
                    <li>Speed: $|v(t)|$</li>
                    <li>Speeding up: $v(t)$ and $a(t)$ same sign</li>
                    <li>Slowing down: $v(t)$ and $a(t)$ opposite signs</li>
                  </ul>

                  <h3 class="text-h6 mb-2 mt-3">Linearization:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>$L(x) = f(a) + f'(a)(x-a)$</li>
                    <li>$f(x) \approx L(x)$ for $x$ near $a$</li>
                  </ul>
                </v-col>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">Related Rates Strategy:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>1. Identify variables and rates</li>
                    <li>2. Find equation relating variables</li>
                    <li>3. Differentiate w.r.t. time (use Chain Rule)</li>
                    <li>4. Substitute known values and solve</li>
                  </ul>

                  <h3 class="text-h6 mb-2 mt-3">L'Hôpital's Rule:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>For $\frac{0}{0}$ or $\frac{\infty}{\infty}$ forms</li>
                    <li>$\lim_{x \to c} \frac{f(x)}{g(x)} = \lim_{x \to c} \frac{f'(x)}{g'(x)}$</li>
                    <li>Verify indeterminate form first</li>
                    <li>Can apply repeatedly if needed</li>
                  </ul>

                  <h3 class="text-h6 mb-2 mt-3">Common Applications:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>Economics: marginal cost/revenue</li>
                    <li>Population: growth rates</li>
                    <li>Geometry: changing dimensions</li>
                  </ul>
                </v-col>
              </v-row>
            </section>

            <v-divider class="my-5"></v-divider>

            <section>
              <h2 class="text-h5 font-weight-medium mb-3">Example: Solving a Related Rates Problem 🤔</h2>
              <p class="text-body-1">
                Air is being pumped into a spherical balloon at a rate of 5 cm³/min. Determine the rate at which the radius of the balloon is increasing when the diameter of the balloon is 20 cm.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 1: Understand and Diagram</strong>
                We have a sphere whose volume and radius are changing with time. Let $V$ be the volume and $r$ be the radius.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 2: Identify Variables and Rates</strong>
                Known rate: Rate of change of volume, $\frac{dV}{dt} = 5 \text{ cm}^3/\text{min}$.
                We want to find: Rate of change of radius, $\frac{dr}{dt}$.
                This is when the diameter is 20 cm, which means the radius $r = 10 \text{ cm}$.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 3: Find an Equation</strong>
                The volume of a sphere is given by $V = \frac{4}{3}\pi r^3$.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 4: Differentiate with Respect to Time $t$</strong>
                Differentiate both sides of $V = \frac{4}{3}\pi r^3$ with respect to $t$:
                $$\frac{d}{dt}[V] = \frac{d}{dt}\left[\frac{4}{3}\pi r^3\right]$$
                $$\frac{dV}{dt} = \frac{4}{3}\pi \cdot 3r^2 \cdot \frac{dr}{dt}$$
                Using the Chain Rule for $r^3$ since $r$ is a function of $t$.
                $$\frac{dV}{dt} = 4\pi r^2 \frac{dr}{dt}$$
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 5: Substitute and Solve</strong>
                Substitute the known values: $\frac{dV}{dt} = 5$ and $r = 10$:
                $$5 = 4\pi (10)^2 \frac{dr}{dt}$$
                $$5 = 4\pi (100) \frac{dr}{dt}$$
                $$5 = 400\pi \frac{dr}{dt}$$
                Now, solve for $\frac{dr}{dt}$:
                $$\frac{dr}{dt} = \frac{5}{400\pi} = \frac{1}{80\pi}$$
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 6: Check and Interpret</strong>
                The rate at which the radius is increasing is $\frac{1}{80\pi}$ cm/min. The units (cm/min) are appropriate for a rate of change of radius.
              </p>
            </section>

          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { onMounted, nextTick } from 'vue';

onMounted(async () => {
  if (window.MathJax) {
    // Wait for the DOM to be fully updated by Vue
    await nextTick();
    // Then typeset MathJax
    if (typeof window.MathJax.typesetPromise === 'function') {
      window.MathJax.typesetPromise();
    } else if (window.MathJax.Hub && typeof window.MathJax.Hub.Queue === 'function') {
      // Fallback for older MathJax versions
      window.MathJax.Hub.Queue(["Typeset", window.MathJax.Hub]);
    }
  }
});
</script>

<style scoped>
/* Add any specific styles for this page if needed */
.text-body-1 ol,
.text-body-1 ul {
  list-style-position: outside;
  padding-left: 20px; /* Indent lists */
}

.text-body-1 ol {
  list-style-type: decimal; /* Or lower-alpha, etc. */
}
.text-body-1 ul {
  list-style-type: disc; /* Or circle, square */
}

section {
  padding: 10px 0;
}

/* Enhance readability of math expressions */
p, li, .text-body-1 {
  line-height: 1.7;
}

.v-card {
  background-color: #fdfdfd; /* Slightly off-white for the card background */
}
</style>