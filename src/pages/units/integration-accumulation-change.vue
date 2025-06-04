<template>
  <v-container class="pa-0 bg-grey-lighten-4" style="min-height: 100vh;" fluid>
    <v-row justify="center" align="start" style="min-height: inherit;" class="py-md-6">
      <v-col cols="12" md="11" lg="9" xl="8">
        <v-card elevation="4" rounded="xl" class="pa-5 pa-md-8">
          <v-card-title class="text-h4 font-weight-bold mb-2 text-primary">Unit 6: Integration and Accumulation of Change</v-card-title>
          <v-card-text>
            <p class="text-body-1 mb-4">
              Unit 6 introduces the concept of <strong>integration</strong>, fundamentally the inverse process of differentiation. You'll explore how integration is used to find the <strong>accumulation of change</strong> and calculate <strong>areas under curves</strong>. Key topics include <strong>Riemann sums</strong> for approximating areas, the profound <strong>Fundamental Theorem of Calculus</strong> which links differentiation and integration, various techniques for finding <strong>antiderivatives</strong> (indefinite integrals), methods for evaluating <strong>definite integrals</strong>, and an introduction to <strong>improper integrals</strong>. This unit lays the foundation for solving a wide array of problems in science, engineering, economics, and beyond.
            </p>

            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="blue-grey-darken-2" class="mr-3 mt-1">mdi-chart-areaspline-variant</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Integration and Accumulation of Change</h2>
                  <div class="text-body-1">
                    If we know the rate at which a quantity changes (a derivative), integration allows us to find the <strong>net change</strong> or <strong>total accumulation</strong> of that quantity over an interval. For example, integrating velocity gives displacement, and integrating a rate of flow gives the total amount flowed. This is a core concept linking derivatives back to original quantities.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="brown-darken-2" class="mr-3 mt-1">mdi-grid</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Approximating Areas with Riemann Sums</h2>
                  <div class="text-body-1">
                    <strong>Riemann Sums</strong> are used to approximate the area between a curve and the x-axis over an interval by summing the areas of geometric shapes (usually rectangles or trapezoids). Common methods include:
                    <ul class="pl-4 mt-1">
                      <li><strong>Left Riemann Sum</strong>: Uses the left endpoint of each subinterval for height.</li>
                      <li><strong>Right Riemann Sum</strong>: Uses the right endpoint.</li>
                      <li><strong>Midpoint Riemann Sum</strong>: Uses the midpoint.</li>
                      <li><strong>Trapezoidal Sum</strong>: Uses the average of left and right endpoint values (forming trapezoids).</li>
                    </ul>
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="deep-purple-darken-2" class="mr-3 mt-1">mdi-sigma</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Riemann Sums, Summation Notation, and Definite Integral Notation</h2>
                  <div class="text-body-1">
                    The <strong>definite integral</strong> $\int_a^b f(x) dx$ represents the exact net signed area between $f(x)$ and the x-axis from $x=a$ to $x=b$. It's defined as the limit of a Riemann sum as the number of subintervals approaches infinity:
                    $$\int_a^b f(x) dx = \lim_{n\to\infty} \sum_{i=1}^n f(x_i^*) \Delta x$$
                    where $\Delta x = \frac{b-a}{n}$ and $x_i^*$ is a point in the $i$-th subinterval.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="light-blue-darken-3" class="mr-3 mt-1">mdi-chart-gantt</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">The Fundamental Theorem of Calculus</h2>
                  <div class="text-body-1">
                    The <strong>Fundamental Theorem of Calculus</strong> connects differentiation and integration through two key parts:
                    <br><br>
                    <strong>Part 1 (Accumulation Functions):</strong> If $g(x) = \int_a^x f(t) dt$, then $g'(x) = f(x)$.
                    This means the derivative of an accumulation function gives back the original function.
                    <br><br>
                    <strong>Part 2 (Evaluation Theorem):</strong> If $F(x)$ is any antiderivative of $f(x)$, then:
                    $$\int_a^b f(x) dx = F(b) - F(a)$$
                    <br>
                    <strong>Behavior of Accumulation Functions:</strong> For $g(x) = \int_a^x f(t) dt$:
                    <ul class="pl-4 mt-1">
                      <li>$g(x)$ increases where $f(x) > 0$, decreases where $f(x) < 0$</li>
                      <li>$g(x)$ has extrema where $f(x)$ changes sign</li>
                      <li>$g(x)$ is concave up/down where $f(x)$ is increasing/decreasing</li>
                    </ul>
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="amber-darken-3" class="mr-3 mt-1">mdi-format-list-numbered</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Properties of Definite Integrals</h2>
                  <div class="text-body-1">
                    Key properties that make integration calculations easier:
                    <ul class="pl-4 mt-1">
                      <li>$\int_a^a f(x)dx = 0$ and $\int_a^b f(x)dx = -\int_b^a f(x)dx$</li>
                      <li>$\int_a^b k \cdot f(x)dx = k \int_a^b f(x)dx$ (constant multiple)</li>
                      <li>$\int_a^b [f(x) \pm g(x)]dx = \int_a^b f(x)dx \pm \int_a^b g(x)dx$ (linearity)</li>
                      <li>$\int_a^c f(x)dx = \int_a^b f(x)dx + \int_b^c f(x)dx$ (additivity)</li>
                    </ul>
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="pink-darken-2" class="mr-3 mt-1">mdi-plus-minus-variant</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Finding Antiderivatives and Indefinite Integrals</h2>
                  <div class="text-body-1">
                    An <strong>antiderivative</strong> of a function $f(x)$ is a function $F(x)$ such that $F'(x) = f(x)$. The set of all antiderivatives of $f(x)$ is called the <strong>indefinite integral</strong>, denoted by:
                    $$\int f(x) dx = F(x) + C$$
                    where $C$ is the constant of integration. Basic rules include the power rule ($\int x^n dx = \frac{x^{n+1}}{n+1} + C$), and integrals of common functions (trigonometric, exponential).
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="teal-darken-3" class="mr-3 mt-1">mdi-swap-horizontal-circle-outline</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Advanced Integration Techniques</h2>
                  <div class="text-body-1">
                    <strong>U-Substitution:</strong> Used when the integrand contains a function and its derivative. Let $u = g(x)$, then $du = g'(x)dx$.
                    <br><br>
                    <strong>Integration by Parts:</strong> For products of functions using $\int u \, dv = uv - \int v \, du$. Use LIATE (Logarithmic, Inverse trig, Algebraic, Trigonometric, Exponential) to choose $u$.
                    <br><br>
                    <strong>Algebraic Manipulation:</strong> Long division for improper rational functions, completing the square for inverse trig forms.
                    <br><br>
                    <strong>Partial Fractions:</strong> Decompose rational functions with factorizable denominators into simpler fractions.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <h2 class="text-h5 font-weight-medium mb-3">Key Formulas & Techniques 🛠️</h2>
              <v-row>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">Core Concepts:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>$\int_a^b f(x) dx = \lim_{n\to\infty} \sum_{i=1}^n f(x_i^*) \Delta x$</li>
                    <li>$\frac{d}{dx} \int_a^x f(t) dt = f(x)$ (FTC Part 1)</li>
                    <li>$\int_a^b f(x) dx = F(b) - F(a)$ (FTC Part 2)</li>
                    <li>$\int f(x) dx = F(x) + C$ (Indefinite integral)</li>
                  </ul>
                  <h3 class="text-h6 mb-2 mt-3">Integration Techniques:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>U-substitution: $u=g(x)$, $du=g'(x)dx$</li>
                    <li>Integration by parts: $\int u \, dv = uv - \int v \, du$</li>
                    <li>Partial fractions for rational functions</li>
                  </ul>
                </v-col>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">Key Properties:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>$\int_a^b k f(x)dx = k\int_a^b f(x)dx$</li>
                    <li>$\int_a^b (f \pm g)dx = \int_a^b f dx \pm \int_a^b g dx$</li>
                    <li>$\int_a^c f dx = \int_a^b f dx + \int_b^c f dx$</li>
                  </ul>
                  <h3 class="text-h6 mb-2 mt-3">Strategy for Choosing Techniques:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>1. Check basic rules first</li>
                    <li>2. Simplify/rewrite if possible</li>
                    <li>3. U-substitution for composite functions</li>
                    <li>4. Integration by parts for products</li>
                    <li>5. Partial fractions for rational functions</li>
                  </ul>
                </v-col>
              </v-row>
            </section>

            <v-divider class="my-5"></v-divider>

            <section>
              <h2 class="text-h5 font-weight-medium mb-3">Example: Integration by Substitution 💡</h2>
              <p class="text-body-1">
                Evaluate the indefinite integral $\int x(x^2+3)^4 dx$.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 1: Choose $u$</strong>
                Observe the integrand. The term $x^2+3$ is raised to a power, and its derivative $2x$ is related to the other factor $x$.
                Let $u = x^2+3$.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 2: Find $du$</strong>
                Differentiate $u$ with respect to $x$:
                $$\frac{du}{dx} = 2x$$
                So, $du = 2x \, dx$.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 3: Substitute into the Integral</strong>
                Our integral is $\int (x^2+3)^4 \cdot x \, dx$.
                We have $u = x^2+3$. We need to replace $x \, dx$. From $du = 2x \, dx$, we can write $x \, dx = \frac{1}{2} du$.
                Substituting these into the integral:
                $$\int u^4 \left(\frac{1}{2} du\right)$$
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 4: Integrate with Respect to $u$</strong>
                $$\frac{1}{2} \int u^4 du = \frac{1}{2} \left( \frac{u^{4+1}}{4+1} \right) + C = \frac{1}{2} \cdot \frac{u^5}{5} + C = \frac{u^5}{10} + C$$
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 5: Substitute Back to $x$</strong>
                Replace $u$ with $x^2+3$:
                $$\frac{(x^2+3)^5}{10} + C$$
                Thus, $\int x(x^2+3)^4 dx = \frac{(x^2+3)^5}{10} + C$.
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