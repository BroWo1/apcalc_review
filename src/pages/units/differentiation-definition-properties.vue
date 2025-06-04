<template>
  <v-container class="pa-0 bg-grey-lighten-4" style="min-height: 100vh;" fluid>
    <v-row justify="center" align="start" style="min-height: inherit;" class="py-md-6">
      <v-col cols="12" md="11" lg="9" xl="8">
        <v-card elevation="4" rounded="xl" class="pa-5 pa-md-8">
          <v-card-title class="text-h4 font-weight-bold mb-2 text-primary">Unit 2: Differentiation: Definition and Fundamental Properties</v-card-title>
          <v-card-text>
        <p class="text-body-1 mb-4">
          Building on the foundation of limits from <strong>Unit 1</strong>, we now explore the powerful concept of the <strong>derivative</strong>, The derivative measures instantaneous rate of change and has applications spanning physics, economics, biology, and beyond. In this unit, you'll master the formal definition of derivatives and learn essential differentiation rules that make calculating derivatives efficient and systematic.
        </p>

        <v-divider class="my-5"></v-divider>

        <section class="mb-6">
          <div class="d-flex align-start">
            <v-icon color="blue-darken-2" class="mr-3 mt-1">mdi-function-variant</v-icon>
            <div class="flex-grow-1">
              <h2 class="text-h5 font-weight-medium mb-2">Definition of a Derivative</h2>
              <div class="text-body-1">
                The derivative of a function $f(x)$ at a specific point $x=a$, denoted as $f'(a)$, is formally defined using a limit. This definition captures the instantaneous rate of change of the function at that point:
                $$f'(a) = \lim_{h \to 0} \frac{f(a+h) - f(a)}{h}$$
                This limit represents how the function's value changes as the interval $h$ around $a$ becomes infinitesimally small. Geometrically, $f'(a)$ gives the precise slope of the line tangent to the graph of $f(x)$ at the point $(a, f(a))$.
              </div>
            </div>
          </div>
        </section>
        <v-divider class="my-5"></v-divider>

        <section class="mb-6">
          <div class="d-flex align-start">
            <v-icon color="green-darken-2" class="mr-3 mt-1">mdi-chart-line</v-icon>
            <div class="flex-grow-1">
              <h2 class="text-h5 font-weight-medium mb-2">Find Derivative Graphically</h2>
              <div class="text-body-1">
                Geometrically, the derivative $f'(a)$ is the slope of the tangent line to the curve $y=f(x)$ at the point $(a, f(a))$. Imagine zooming in on the curve at that point until it looks like a straight line; the slope of this line is the derivative. This provides a powerful visual understanding of how a function is changing at any specific point. A positive derivative means the function is increasing, a negative derivative means it's decreasing, and a zero derivative often indicates a horizontal tangent (like at a peak or valley).
              </div>
            </div>
          </div>
        </section>
        <v-divider class="my-5"></v-divider>

        <section class="mb-6">
          <div class="d-flex align-start">
            <v-icon color="orange-darken-2" class="mr-3 mt-1">mdi-speedometer</v-icon>
            <div class="flex-grow-1">
              <h2 class="text-h5 font-weight-medium mb-2">Derivative in Physics</h2>
              <div class="text-body-1">
                In many scientific applications, particularly physics, the derivative has a very tangible meaning. If $s(t)$ represents the position of an object at time $t$, then its derivative, $s'(t)$ (often written as $v(t)$), represents the object's instantaneous velocity at time $t$. Taking the derivative again, $s''(t)$ or $v'(t)$ (often written as $a(t)$), gives the instantaneous acceleration, which is the rate of change of velocity. This concept extends to other fields, like economics (marginal cost/revenue) or biology (population growth rates).
              </div>
            </div>
          </div>
        </section>
        <v-divider class="my-5"></v-divider>

        <section class="mb-6">
          <div class="d-flex align-start">
            <v-icon color="purple-darken-2" class="mr-3 mt-1">mdi-check-circle-outline</v-icon>
            <div class="flex-grow-1">
              <h2 class="text-h5 font-weight-medium mb-2">Differentiability and Continuity</h2>
              <div class="text-body-1">
                A crucial relationship exists: if a function is differentiable at a point $x=c$, then it <strong>must</strong> be continuous at $x=c$. You can't have a defined slope (derivative) if there's a break or jump in the graph. However, the reverse is not always true: a function can be continuous at a point but not differentiable there. Common examples include functions with sharp corners (like $f(x) = |x|$ at $x=0$), cusps, or vertical tangent lines. At these points, the limit defining the derivative does not exist.
              </div>
            </div>
          </div>
        </section>
        <v-divider class="my-5"></v-divider>

        <section class="mb-6">
          <div class="d-flex align-start">
            <v-icon color="red-darken-2" class="mr-3 mt-1">mdi-calculator</v-icon>
            <div class="flex-grow-1">
              <h2 class="text-h5 font-weight-medium mb-2">Fundamental Rules for Differentiation</h2>
              <div class="text-body-1">
                While the limit definition is fundamental, calculating derivatives this way for every function would be tedious. Fortunately, we have a set of rules that streamline the process. These include:
                <ul class="pl-4 mt-1">
                  <li><strong>Constant Rule:</strong> The derivative of a constant is 0.</li>
                  <li><strong>Power Rule:</strong> For $\frac{d}{dx}[x^n] = nx^{n-1}$.</li>
                  <li><strong>Constant Multiple Rule:</strong> $\frac{d}{dx}[cf(x)] = c \cdot f'(x)$.</li>
                  <li><strong>Sum and Difference Rules:</strong> $\frac{d}{dx}[f(x) \pm g(x)] = f'(x) \pm g'(x)$.</li>
                </ul>
                These rules are the building blocks for differentiating more complex functions.
              </div>
            </div>
          </div>
        </section>
        <v-divider class="my-5"></v-divider>

        <section class="mb-6">
          <div class="d-flex align-start">
            <v-icon color="teal-darken-2" class="mr-3 mt-1">mdi-function</v-icon>
            <div class="flex-grow-1">
              <h2 class="text-h5 font-weight-medium mb-2">Common Derivatives</h2>
              <div class="text-body-1">
                Beyond the basic rules, it's essential to know the derivatives of several standard functions, as they appear frequently. These include:
                <ul class="pl-4 mt-1">
                  <li>Polynomials (derived using the Power Rule)</li>
                  <li>Exponential functions (e.g., $\frac{d}{dx}[e^x] = e^x$)</li>
                  <li>Logarithmic functions (e.g., $\frac{d}{dx}[\ln x] = \frac{1}{x}$)</li>
                  <li>Trigonometric functions (e.g., $\frac{d}{dx}[\sin x] = \cos x$, $\frac{d}{dx}[\cos x] = -\sin x$)</li>
                </ul>
                Memorizing these, or knowing how to quickly derive them, is key for efficient problem-solving.
              </div>
            </div>
          </div>
        </section>

        <v-divider class="my-5"></v-divider>

        <section class="mb-6">
          <h2 class="text-h5 font-weight-medium mb-3">Key Formulas & Rules 📝</h2>
          <v-row>
            <v-col cols="12" md="6">
              <h3 class="text-h6 mb-2">Definition & Notation:</h3>
              <ul class="pl-5 text-body-2">
                <li>Definition: $f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$</li>
                <li>Alternative: $f'(x) = \lim_{\Delta x \to 0} \frac{\Delta y}{\Delta x}$</li>
                <li>Leibniz notation: $\frac{dy}{dx}$ or $\frac{d}{dx}[f(x)]$</li>
                <li>Prime notation: $f'(x)$, $y'$</li>
              </ul>

              <h3 class="text-h6 mb-2 mt-3">Basic Rules:</h3>
              <ul class="pl-5 text-body-2">
                <li>Constant Rule: $\frac{d}{dx}[c] = 0$</li>
                <li>Power Rule: $\frac{d}{dx}[x^n] = nx^{n-1}$</li>
                <li>Constant Multiple: $\frac{d}{dx}[cf(x)] = cf'(x)$</li>
                <li>Sum/Difference: $\frac{d}{dx}[f(x) \pm g(x)] = f'(x) \pm g'(x)$</li>
              </ul>
            </v-col>
            <v-col cols="12" md="6">
              <h3 class="text-h6 mb-2">Common Derivatives:</h3>
              <ul class="pl-5 text-body-2">
                <li>$\frac{d}{dx}[x^n] = nx^{n-1}$ (Power Rule)</li>
                <li>$\frac{d}{dx}[e^x] = e^x$</li>
                <li>$\frac{d}{dx}[\ln x] = \frac{1}{x}$</li>
                <li>$\frac{d}{dx}[\sin x] = \cos x$</li>
                <li>$\frac{d}{dx}[\cos x] = -\sin x$</li>
                <li>$\frac{d}{dx}[\tan x] = \sec^2 x$</li>
              </ul>

              <h3 class="text-h6 mb-2 mt-3">Higher-Order Derivatives:</h3>
              <ul class="pl-5 text-body-2">
                <li>Second derivative: $f''(x)$ or $\frac{d^2y}{dx^2}$</li>
                <li>Third derivative: $f'''(x)$ or $\frac{d^3y}{dx^3}$</li>
                <li>$n$th derivative: $f^{(n)}(x)$ or $\frac{d^ny}{dx^n}$</li>
              </ul>
            </v-col>
          </v-row>
        </section>

        <v-divider class="my-5"></v-divider>

        <section>
          <h2 class="text-h5 font-weight-medium mb-3">Example: Using the Definition 🤔</h2>
          <p class="text-body-1">
            Let's find the derivative of $f(x) = x^2$ using the formal definition to see how the Power Rule emerges naturally.
          </p>
          <p class="text-body-1 mt-2">
            <strong>Step 1:</strong> Apply the definition of the derivative:
            $$f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$$
          </p>
          <p class="text-body-1 mt-2">
            <strong>Step 2:</strong> Substitute $f(x) = x^2$:
            $$f'(x) = \lim_{h \to 0} \frac{(x+h)^2 - x^2}{h}$$
          </p>
          <p class="text-body-1 mt-2">
            <strong>Step 3:</strong> Expand $(x+h)^2$:
            $$f'(x) = \lim_{h \to 0} \frac{x^2 + 2xh + h^2 - x^2}{h} = \lim_{h \to 0} \frac{2xh + h^2}{h}$$
          </p>
          <p class="text-body-1 mt-2">
            <strong>Step 4:</strong> Factor out $h$ and simplify:
            $$f'(x) = \lim_{h \to 0} \frac{h(2x + h)}{h} = \lim_{h \to 0} (2x + h)$$
          </p>
          <p class="text-body-1 mt-2">
            <strong>Step 5:</strong> Evaluate the limit:
            $$f'(x) = 2x + 0 = 2x$$
          </p>
          <p class="text-body-1 mt-2">
            Therefore, if $f(x) = x^2$, then $f'(x) = 2x$. This confirms the Power Rule: $\frac{d}{dx}[x^n] = nx^{n-1}$ for $n=2$.
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
