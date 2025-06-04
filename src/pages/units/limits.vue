<template>
  <v-container class="pa-0 bg-grey-lighten-4" style="min-height: 100vh;" fluid>
    <v-row justify="center" align="start" style="min-height: inherit;" class="py-md-6">
      <v-col cols="12" md="11" lg="9" xl="8">
        <v-card elevation="4" rounded="xl" class="pa-5 pa-md-8">
          <v-card-title class="text-h4 font-weight-bold mb-2 text-primary">Unit 1: Limits & Continuity</v-card-title>
          <v-card-text>
            <p class="text-body-1 mb-4">
              Welcome to the foundational unit of AP Calculus! Here, we'll explore the crucial concepts of **limits** and **continuity**. Understanding limits allows us to analyze the behavior of functions, while continuity helps us identify functions that are well-behaved without breaks or jumps. These ideas are the bedrock upon which differential calculus (derivatives) is built.
            </p>

            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="blue-darken-2" class="mr-3 mt-1">mdi-ideogram-cjk-variant</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Definition of a Limit</h2>
                  <div class="text-body-1">
                    A limit describes the behavior of a function $f(x)$ as its input $x$ gets closer and closer to a particular point $c$. If the function's output values approach a specific number $L$, we say the limit of $f(x)$ as $x$ approaches $c$ is $L$. This is written as: $$\lim_{x \to c} f(x) = L$$ Essentially, we can make $f(x)$ as close to $L$ as we want, simply by choosing an $x$ sufficiently near $c$, without $x$ actually being $c$.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="green-darken-2" class="mr-3 mt-1">mdi-calculator-variant-outline</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Finding Limit Graphically</h2>
                  <div class="text-body-1">
                    Limits can often be estimated by examining a function's graph or a table of its values. By observing the function's behavior as $x$ approaches $c$ from both the left side (denoted $x \to c^-$) and the right side (denoted $x \to c^+$), we can predict the limit. If the function approaches the same value $L$ from both directions, i.e., $\lim_{x \to c^-} f(x) = \lim_{x \to c^+} f(x) = L$, then the overall limit $\lim_{x \to c} f(x)$ is $L$.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="orange-darken-2" class="mr-3 mt-1">mdi-puzzle-edit-outline</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Finding Limits algebraically</h2>
                  <div class="text-body-1">
                    While estimation is useful, precise limit values are often found using algebraic techniques. These include direct substitution, factoring expressions, rationalizing numerators or denominators, simplifying complex fractions, and applying established limit properties. These methods are particularly vital when dealing with indeterminate forms such as $\frac{0}{0}$ or $\frac{\infty}{\infty}$. For instance, consider the limit $\lim_{x \to 2} \frac{x^2 - 4}{x - 2}$.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="purple-darken-2" class="mr-3 mt-1">mdi-link-variant</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Determine Continuity</h2>
                  <div class="text-body-1">
                    A function $f(x)$ is considered continuous at a specific point $x=c$ if it meets all three of the following conditions. If any condition fails, the function is discontinuous at $x=c$.
                    <ol class="pl-4 mt-1 mb-2">
                      <li>$f(c)$ is defined (the point exists on the graph; $c$ is in the domain of $f$). Without a defined point, there's nothing to be continuous *at*.</li>
                      <li>$\lim_{x \to c} f(x)$ exists (the function approaches the same finite value from both the left and the right). If the function approaches different values or tends towards infinity, it's not settling towards a specific point.</li>
                      <li>$\lim_{x \to c} f(x) = f(c)$ (the limit value the function approaches is the actual function value at that point). The function must go where it's "aiming".</li>
                    </ol>
                    A function is continuous on an interval if it is continuous at every point in that interval. Visually, a continuous function can be drawn without lifting your pencil.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="brown-darken-2" class="mr-3 mt-1">mdi-image-broken-variant</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Types of Discontinuities</h2>
                  <div class="text-body-1">
                    If a function fails to be continuous at a point $x=c$, it is said to have a discontinuity there. These breaks in the function can be categorized into several common types:
                    <ul class="pl-4 mt-1">
                      <li><strong>Removable Discontinuity (Hole):</strong> Occurs if $\lim_{x \to c} f(x)$ exists but is not equal to $f(c)$ (either because $f(c)$ is undefined or has a different value). Graphically, this looks like a hole in the graph that could be "filled" by redefining $f(c)$ to be equal to the limit. Example: $f(x) = \frac{x^2-4}{x-2}$ at $x=2$. The limit as $x \to 2$ is 4, but $f(2)$ is undefined.</li>
                      <li><strong>Jump Discontinuity:</strong> Occurs if the left-hand limit and the right-hand limit both exist (are finite) but are not equal: $\lim_{x \to c^-} f(x) \neq \lim_{x \to c^+} f(x)$. The graph "jumps" from one y-value to another. Example: Piecewise functions often exhibit jumps.</li>
                      <li><strong>Infinite Discontinuity (Asymptotic):</strong> Occurs if one or both of the one-sided limits approach $\infty$ or $-\infty$ as $x \to c$. This is typically associated with a vertical asymptote at $x=c$. Example: $f(x) = \frac{1}{x}$ at $x=0$.</li>
                    </ul>
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="red-darken-2" class="mr-3 mt-1">mdi-chart-timeline-variant</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">The Intermediate Value Theorem (IVT)</h2>
                  <div class="text-body-1">
                    The Intermediate Value Theorem (IVT) is a powerful result for continuous functions. It states that if a function $f$ is **continuous** over a **closed interval** $[a, b]$, and $N$ is any number strictly between $f(a)$ and $f(b)$ (assuming $f(a)$ and $f(b)$ are different), then there must exist at least one number $c$ in the **open interval** $(a, b)$ such that $f(c) = N$. In other words, $f(c) = N$.
                    <br/><strong>Intuition:</strong> If you draw a continuous curve from a point $(a, f(a))$ to $(b, f(b))$ without lifting your pen, you must cross every horizontal line $y=N$ that lies between the y-values of your starting and ending points.
                    <br/><strong>Key Conditions:</strong>
                    <ul class="pl-4 mt-1">
                        <li><strong>Continuity is essential:</strong> If there's a break (discontinuity) in the function on the interval, it might "jump over" the value $N$.</li>
                        <li>Closed interval $[a,b]$ is required for evaluating $f(a)$ and $f(b)$:** The function must be defined at the endpoints to establish the range of y-values.</li>
                    </ul>
                    The IVT is an existence theorem; it tells you such a $c$ exists, but not how to find it. It's commonly used to prove the existence of roots for equations.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="teal-darken-2" class="mr-3 mt-1">mdi-infinity</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Limits and Asymptotes</h2>
                  <div class="text-body-1">
                    Limits can also describe a function's behavior as $x$ grows infinitely large ($x \to \infty$) or infinitely small ($x \to -\infty$). These are known as limits at infinity and help us understand the function's end behavior and identify horizontal asymptotes. Conversely, some limits result in $\infty$ or $-\infty$, which often signify the presence of vertical asymptotes. For instance, $\lim_{x \to \infty} \frac{1}{x} = 0$ illustrates end behavior, while $\lim_{x \to 0^+} \frac{1}{x} = \infty$ indicates a vertical asymptote.
                  </div>
                </div>
              </div>
            </section>

            <v-divider class="my-5"></v-divider>
            <section class="mb-6">
              <h2 class="text-h5 font-weight-medium mb-3">Your Toolkit: Essential Limit Formulas & Properties 📝</h2>
              <v-row>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">Limit Properties:</h3>
                  <p>Assuming $\lim_{x \to c} f(x) = L$ and $\lim_{x \to c} g(x) = M$ (where L and M are finite numbers):</p>
                  <ul class="pl-5 text-body-2">
                    <li>Sum/Difference: $\lim_{x \to c} [f(x) \pm g(x)] = L \pm M$</li>
                    <li>Constant Multiple: $\lim_{x \to c} [k \cdot f(x)] = kL$ (for any constant k)</li>
                    <li>Product: $\lim_{x \to c} [f(x)g(x)] = LM$</li>
                    <li>Quotient: $\lim_{x \to c} \frac{f(x)}{g(x)} = \frac{L}{M}$, provided $M \neq 0$</li>
                    <li>Power: $\lim_{x \to c} [f(x)]^n = L^n$ (for any rational exponent $n$, provided $L^n$ is defined)</li>
                    <li>Root: $\lim_{x \to c} \sqrt[n]{f(x)} = \sqrt[n]{L}$ (if $n$ is even, assume $L \ge 0$)</li>
                  </ul>
                </v-col>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">Important Trigonometric Limits:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>$\lim_{x \to 0} \frac{\sin x}{x} = 1$</li>
                    <li>$\lim_{x \to 0} \frac{1 - \cos x}{x} = 0$ (or equivalently, $\lim_{x \to 0} \frac{\cos x - 1}{x} = 0$)</li>
                  </ul>
                  <h3 class="text-h6 mb-2 mt-3">Definition of $e$:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>$\lim_{x \to \infty} \left(1 + \frac{1}{x}\right)^x = e$</li>
                    <li>$\lim_{n \to 0} (1 + n)^{1/n} = e$</li>
                  </ul>
                </v-col>
              </v-row>
            </section>

            <v-divider class="my-5"></v-divider>

            <section>
              <h2 class="text-h5 font-weight-medium mb-3">IVT in Action: Finding a Root 🤔</h2>
              <p class="text-body-1">
                Consider the function $f(x) = x^3 - x - 1$. We want to show that there is a root (a value of $x$ for which $f(x) = 0$) between $x=1$ and $x=2$.
              </p>
              <p class="text-body-1 mt-2">
                1.  <strong>Continuity:</strong> $f(x)$ is a polynomial function. Polynomial functions are continuous everywhere, so $f(x)$ is continuous on the closed interval $[1, 2]$. This is a critical first step to verify.
              </p>
              <p class="text-body-1 mt-2">
                2.  <strong>Function Values at Endpoints:</strong>
                <ul class="pl-4">
                  <li>$f(1) = 1^3 - 1 - 1 = 1 - 1 - 1 = -1$</li>
                  <li>$f(2) = 2^3 - 2 - 1 = 8 - 2 - 1 = 5$</li>
                </ul>
              </p>
              <p class="text-body-1 mt-2">
                3.  <strong>Target Value $N$:</strong> We are looking for a root, so we want to find an $x$ such that $f(x)=0$. Thus, our target intermediate value is $N=0$.
              </p>
              <p class="text-body-1 mt-2">
                4.  <strong>Apply IVT:</strong>
                Since $f(x)$ is continuous on $[1, 2]$, $f(1) = -1$, and $f(2) = 5$. The value $N=0$ is between $f(1)$ and $f(2)$ (i.e., $-1 < 0 < 5$).
                Therefore, by the Intermediate Value Theorem, there must be at least one value $c$ in the open interval $(1, 2)$ such that $f(c) = 0$.
              </p>
              <p class="text-body-1 mt-2">
                This confirms there is a root of $f(x) = x^3 - x - 1$ between $x=1$ and $x=2$. The IVT guarantees its existence but doesn't provide the exact value of $c$.
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
  list-style-type: decimal;
}
.text-body-1 ul {
  list-style-type: disc; /* Or circle, square */
}


.v-card {
  background-color: #fdfdfd; /* Slightly off-white for the card background */
}

section {
  padding: 10px 0;
}

/* Enhance readability of math expressions */
p, li, .text-body-1 {
  line-height: 1.7;
}

h3.text-h6 {
  font-weight: 500; /* Make subheadings slightly bolder */
  color: #333; /* Darker color for subheadings */
}
</style>