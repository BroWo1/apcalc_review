<template>
  <v-container class="pa-0 bg-grey-lighten-4" style="min-height: 100vh;" fluid>
    <v-row justify="center" align="start" style="min-height: inherit;" class="py-md-6">
      <v-col cols="12" md="11" lg="9" xl="8">
        <v-card elevation="4" rounded="xl" class="pa-5 pa-md-8">
          <v-card-title class="text-h4 font-weight-bold mb-2 text-primary">Unit 3: Differentiation: Composite, Implicit, and Inverse Functions</v-card-title>
          <v-card-text>
            <p class="text-body-1 mb-4">
              Building upon the differentiation rules from <strong>Unit 2</strong>, this unit significantly expands your differentiation toolkit. You’ll master the crucial <strong>Chain Rule</strong> for differentiating composite functions (functions of functions), explore <strong>Implicit Differentiation</strong> for situations where functions are not explicitly solved for a variable, and learn how to find derivatives of <strong>Inverse Functions</strong>, including common inverse trigonometric functions. Furthermore, we'll delve into strategies for selecting the most effective differentiation procedures and introduce the concept of <strong>Higher-Order Derivatives</strong>, opening doors to a deeper analysis of function behavior and their rates of change.
            </p>

            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="blue-darken-2" class="mr-3 mt-1">mdi-link-variant</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">The Chain Rule</h2>
                  <div class="text-body-1">
                    The <strong>Chain Rule</strong> is a fundamental formula for differentiating composite functions. If you have a function that is a function of another function (e.g., $y = f(g(x))$), the Chain Rule provides a way to find its derivative. It's essential because many real-world models involve nested functions.
                    The rule states that if $y = f(u)$ and $u = g(x)$, then the derivative of $y$ with respect to $x$ is:
                    $$\frac{dy}{dx} = \frac{dy}{du} \cdot \frac{du}{dx}$$
                    Alternatively, for a composite function $h(x) = f(g(x))$, its derivative is:
                    $$h'(x) = f'(g(x)) \cdot g'(x)$$
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="green-darken-2" class="mr-3 mt-1">mdi-vector-curve</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Solve Implicit Differentiation</h2>
                  <div class="text-body-1">
                    Sometimes, a relationship between $x$ and $y$ is defined implicitly by an equation, like $x^2 + y^2 = 25$, rather than explicitly as $y = f(x)$. <strong>Implicit Differentiation</strong> allows us to find $\frac{dy}{dx}$ without first solving for $y$. The process involves:
                    <ol class="pl-4 mt-1">
                      <li>Differentiating both sides of the equation with respect to $x$.</li>
                      <li>Remembering that $y$ is a function of $x$, so when differentiating terms containing $y$, apply the Chain Rule (e.g., $\frac{d}{dx}[y^2] = 2y \frac{dy}{dx}$).</li>
                      <li>Solving the resulting equation algebraically for $\frac{dy}{dx}$.</li>
                    </ol>
                    This technique is crucial for finding slopes of tangent lines to curves that are not easily expressed as functions of $x$.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="orange-darken-2" class="mr-3 mt-1">mdi-swap-horizontal-bold</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">The Derivative of Inverse Functions</h2>
                  <div class="text-body-1">
                    If a function $f$ has an inverse $f^{-1}$ (also denoted as $g$), there's a direct relationship between their derivatives. If $f(a)=b$, then $f^{-1}(b)=a$. The derivative of the inverse function $f^{-1}$ at a point $x=b$ is the reciprocal of the derivative of the original function $f$ evaluated at $f^{-1}(b)$ (which is $a$).
                    Formally, if $g(x) = f^{-1}(x)$, then:
                    $$g'(x) = \frac{1}{f'(g(x))}$$
                    Provided $f'(g(x)) \neq 0$. This rule is powerful because it allows us to find the derivative of an inverse function even if we don't have an explicit formula for the inverse function itself. Geometrically, the slope of the tangent to $f^{-1}$ at $(b,a)$ is the reciprocal of the slope of the tangent to $f$ at $(a,b)$.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="purple-darken-2" class="mr-3 mt-1">mdi-chart-arc</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Derivatives of Inverse Trigonometric Functions</h2>
                  <div class="text-body-1">
                    Using the rule for differentiating inverse functions (and sometimes implicit differentiation), we can derive standard formulas for the derivatives of inverse trigonometric functions. These are important as these functions appear in various applications, especially when dealing with angles or integrating certain algebraic forms. Key derivatives include:
                    <ul class="pl-4 mt-1">
                      <li>$\frac{d}{dx}[\arcsin x] = \frac{1}{\sqrt{1-x^2}}$</li>
                      <li>$\frac{d}{dx}[\arccos x] = -\frac{1}{\sqrt{1-x^2}}$</li>
                      <li>$\frac{d}{dx}[\arctan x] = \frac{1}{1+x^2}$</li>
                      <li>$\frac{d}{dx}[\text{arccot } x] = -\frac{1}{1+x^2}$</li>
                      <li>$\frac{d}{dx}[\text{arcsec } x] = \frac{1}{|x|\sqrt{x^2-1}}$</li>
                      <li>$\frac{d}{dx}[\text{arccsc } x] = -\frac{1}{|x|\sqrt{x^2-1}}$</li>
                    </ul>
                    It's useful to memorize these or know how to derive them.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="red-darken-2" class="mr-3 mt-1">mdi-clipboard-check-outline</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Choosing Differentiation Technique</h2>
                  <div class="text-body-1">
                    With a growing arsenal of differentiation rules (Power, Product, Quotient, Chain Rules, implicit differentiation, derivatives of specific functions like trigonometric, exponential, logarithmic, and their inverses), it's crucial to develop a strategy for approaching differentiation problems.
                    The key is to carefully analyze the structure of the function you need to differentiate:
                    <ul class="pl-4 mt-1">
                      <li>Is it a sum or difference? Use the Sum/Difference Rule.</li>
                      <li>Is it a product? Use the Product Rule.</li>
                      <li>Is it a quotient? Use the Quotient Rule.</li>
                      <li>Is it a composite function (a function of a function)? Use the Chain Rule. Often, this is combined with other rules.</li>
                      <li>Is the relationship between variables implicit? Use Implicit Differentiation.</li>
                      <li>Does it involve standard functions whose derivatives are known? Apply those directly.</li>
                    </ul>
                    Many problems require a combination of these rules. Practice is key to recognizing patterns and applying the correct procedures efficiently.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="teal-darken-2" class="mr-3 mt-1">mdi-layers-outline</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Finding Higher Order Derivatives</h2>
                  <div class="text-body-1">
                    The derivative of a function $f(x)$, denoted $f'(x)$ or $\frac{dy}{dx}$, is itself a function. We can differentiate this new function again to find the <strong>second derivative</strong>, denoted $f''(x)$ or $\frac{d^2y}{dx^2}$. This process can be repeated to find the third derivative ($f'''(x)$ or $\frac{d^3y}{dx^3}$), fourth derivative ($f^{(4)}(x)$ or $\frac{d^4y}{dx^4}$), and so on, leading to <strong>higher-order derivatives</strong>.
                    For example, if $s(t)$ is the position of an object at time $t$:
                    <ul class="pl-4 mt-1">
                      <li>$s'(t) = v(t)$ is the velocity (first derivative).</li>
                      <li>$s''(t) = v'(t) = a(t)$ is the acceleration (second derivative).</li>
                      <li>$s'''(t) = a'(t) = j(t)$ is the jerk (third derivative), representing the rate of change of acceleration.</li>
                    </ul>
                    Higher-order derivatives provide deeper insights into the behavior of functions, such as concavity (related to the second derivative) and other rates of change.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <h2 class="text-h5 font-weight-medium mb-3">Key Formulas & Rules 📝</h2>
              <v-row>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">Chain Rule:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>If $y=f(u)$ and $u=g(x)$: $\frac{dy}{dx} = \frac{dy}{du} \cdot \frac{du}{dx}$</li>
                    <li>For $h(x) = f(g(x))$: $h'(x) = f'(g(x)) \cdot g'(x)$</li>
                  </ul>

                  <h3 class="text-h6 mb-2 mt-3">Implicit Differentiation:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>Differentiate both sides of $F(x,y)=C$ w.r.t. $x$.</li>
                    <li>Treat $y$ as $y(x)$, use Chain Rule for terms with $y$.</li>
                    <li>Solve for $\frac{dy}{dx}$.</li>
                  </ul>

                  <h3 class="text-h6 mb-2 mt-3">Derivative of an Inverse Function:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>If $g(x) = f^{-1}(x)$: $g'(x) = \frac{1}{f'(g(x))}$</li>
                  </ul>
                </v-col>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">Inverse Trigonometric Derivatives:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>$\frac{d}{dx}[\arcsin x] = \frac{1}{\sqrt{1-x^2}}$</li>
                    <li>$\frac{d}{dx}[\arccos x] = -\frac{1}{\sqrt{1-x^2}}$</li>
                    <li>$\frac{d}{dx}[\arctan x] = \frac{1}{1+x^2}$</li>
                    <li>$\frac{d}{dx}[\text{arccot } x] = -\frac{1}{1+x^2}$</li>
                    <li>$\frac{d}{dx}[\text{arcsec } x] = \frac{1}{|x|\sqrt{x^2-1}}$</li>
                    <li>$\frac{d}{dx}[\text{arccsc } x] = -\frac{1}{|x|\sqrt{x^2-1}}$</li>
                  </ul>

                  <h3 class="text-h6 mb-2 mt-3">Higher-Order Derivatives Notation:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>Second: $f''(x)$, $\frac{d^2y}{dx^2}$</li>
                    <li>Third: $f'''(x)$, $\frac{d^3y}{dx^3}$</li>
                    <li>$n$th: $f^{(n)}(x)$, $\frac{d^ny}{dx^n}$</li>
                  </ul>
                </v-col>
              </v-row>
            </section>

            <v-divider class="my-5"></v-divider>

            <section>
              <h2 class="text-h5 font-weight-medium mb-3">Example: Applying the Chain Rule 🤔</h2>
              <p class="text-body-1">
                Let's find the derivative of $y = (2x^3 + 5x - 1)^4$ using the Chain Rule.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 1:</strong> Identify the outer function and the inner function.
                Let the outer function be $f(u) = u^4$ and the inner function be $u(x) = 2x^3 + 5x - 1$.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 2:</strong> Find the derivatives of the outer and inner functions.
                $$f'(u) = \frac{d}{du}[u^4] = 4u^3$$
                $$u'(x) = \frac{d}{dx}[2x^3 + 5x - 1] = 6x^2 + 5$$
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 3:</strong> Apply the Chain Rule formula: $\frac{dy}{dx} = f'(u(x)) \cdot u'(x)$.
                Substitute $u(x)$ back into $f'(u)$:
                $$f'(u(x)) = 4(2x^3 + 5x - 1)^3$$
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 4:</strong> Multiply $f'(u(x))$ by $u'(x)$:
                $$\frac{dy}{dx} = 4(2x^3 + 5x - 1)^3 \cdot (6x^2 + 5)$$
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 5:</strong> Simplify (optional, often left in factored form for clarity):
                $$\frac{dy}{dx} = (24x^2 + 20)(2x^3 + 5x - 1)^3$$
              </p>
              <p class="text-body-1 mt-2">
                Thus, the derivative of $y = (2x^3 + 5x - 1)^4$ is $(24x^2 + 20)(2x^3 + 5x - 1)^3$.
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