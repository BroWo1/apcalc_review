<template>
  <v-container class="pa-0 bg-grey-lighten-4" style="min-height: 100vh;" fluid>
    <v-row justify="center" align="start" style="min-height: inherit;" class="py-md-6">
      <v-col cols="12" md="11" lg="9" xl="8">
        <v-card elevation="4" rounded="xl" class="pa-5 pa-md-8">
          <v-card-title class="text-h4 font-weight-bold mb-2 text-primary">Unit 5: Analytical Applications of Differentiation</v-card-title>
          <v-card-text>
            <p class="text-body-1 mb-4">
              Unit 5 delves into the analytical power of derivatives to understand the behavior of functions in depth. You'll learn to apply theorems like the <strong>Mean Value Theorem</strong> and <strong>Extreme Value Theorem</strong>, use derivatives to find intervals of <strong>increase/decrease</strong>, locate <strong>extrema</strong> (maximums and minimums), determine <strong>concavity</strong> and <strong>inflection points</strong>, and <strong>sketch curves</strong>. This unit culminates in applying these techniques to solve <strong>optimization problems</strong> and analyze <strong>implicit relations</strong>, providing a robust framework for function analysis.
            </p>

            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="blue-darken-2" class="mr-3 mt-1">mdi-chart-line-variant</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">The Mean Value Theorem (MVT)</h2>
                  <div class="text-body-1">
                    The <strong>Mean Value Theorem</strong> states that if a function $f$ is continuous on a closed interval $[a,b]$ and differentiable on the open interval $(a,b)$, then there exists at least one number $c$ in $(a,b)$ such that:
                    $$f'(c) = \frac{f(b) - f(a)}{b-a}$$
                    Geometrically, this means there's a point $c$ where the slope of the tangent line is equal to the slope of the secant line through $(a,f(a))$ and $(b,f(b))$. It's a crucial theorem for proving other results in calculus.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="green-darken-2" class="mr-3 mt-1">mdi-peak</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Extreme Value Theorem, Global vs Local Extrema, and Critical Points</h2>
                  <div class="text-body-1">
                    The <strong>Extreme Value Theorem (EVT)</strong> guarantees that if a function $f$ is continuous on a closed interval $[a,b]$, then $f$ must attain an <strong>absolute (global) maximum</strong> and an <strong>absolute (global) minimum</strong> value on that interval.
                    <ul class="pl-4 mt-1">
                      <li><strong>Local (Relative) Extrema</strong>: Maximum or minimum values in some open interval around a point.</li>
                      <li><strong>Global (Absolute) Extrema</strong>: The overall maximum or minimum values of the function over its entire domain or a specified interval.</li>
                      <li><strong>Critical Points</strong>: Points $c$ in the domain of $f$ where $f'(c) = 0$ or $f'(c)$ is undefined. Extrema can only occur at critical points or endpoints of an interval.</li>
                    </ul>
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="orange-darken-2" class="mr-3 mt-1">mdi-chart-areaspline</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Intervals Increasing or Decreasing</h2>
                  <div class="text-body-1">
                    The first derivative $f'(x)$ tells us about the rate of change of $f(x)$:
                    <ul class="pl-4 mt-1">
                      <li>If $f'(x) > 0$ on an interval, then $f$ is <strong>increasing</strong> on that interval.</li>
                      <li>If $f'(x) < 0$ on an interval, then $f$ is <strong>decreasing</strong> on that interval.</li>
                      <li>If $f'(x) = 0$ on an interval, then $f$ is <strong>constant</strong> on that interval.</li>
                    </ul>
                    To find these intervals, determine critical points and test the sign of $f'(x)$ in the intervals created by these points.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="red-darken-2" class="mr-3 mt-1">mdi-numeric-1-box-multiple-outline</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Finding and Classifying Extrema</h2>
                  <div class="text-body-1">
                    <strong>First Derivative Test:</strong> Uses sign changes of $f'(x)$ around critical point $c$:
                    <ul class="pl-4 mt-1">
                      <li>$f'$ changes + to − → <strong>local maximum</strong> at $c$</li>
                      <li>$f'$ changes − to + → <strong>local minimum</strong> at $c$</li>
                      <li>No sign change → no local extremum at $c$</li>
                    </ul>
                    <br>
                    <strong>Second Derivative Test:</strong> Alternative method when $f'(c) = 0$:
                    <ul class="pl-4 mt-1">
                      <li>$f''(c) > 0$ → <strong>local minimum</strong> (concave up)</li>
                      <li>$f''(c) < 0$ → <strong>local maximum</strong> (concave down)</li>
                      <li>$f''(c) = 0$ → inconclusive, use First Derivative Test</li>
                    </ul>
                    <br>
                    <strong>Candidates Test (Absolute Extrema on [a,b]):</strong>
                    <ol class="pl-4 mt-1">
                      <li>Find critical points in $(a,b)$ and evaluate $f$ at these points</li>
                      <li>Evaluate $f$ at endpoints $a$ and $b$</li>
                      <li>Compare all values: largest = absolute max, smallest = absolute min</li>
                    </ol>
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="teal-darken-2" class="mr-3 mt-1">mdi-shape-outline</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Concavity and Points of Inflection</h2>
                  <div class="text-body-1">
                    The second derivative $f''(x)$ determines concavity:
                    <ul class="pl-4 mt-1">
                      <li>$f''(x) > 0$ → <strong>concave upward</strong> (cup shape)</li>
                      <li>$f''(x) < 0$ → <strong>concave downward</strong> (frown shape)</li>
                    </ul>
                    <br>
                    <strong>Points of Inflection:</strong> Where concavity changes. At point $(c, f(c))$:
                    <ul class="pl-4 mt-1">
                      <li>$f''(c) = 0$ or undefined</li>
                      <li>$f''(x)$ changes sign around $x = c$</li>
                    </ul>
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="cyan-darken-2" class="mr-3 mt-1">mdi-link-box-variant-outline</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Function Analysis and Applications</h2>
                  <div class="text-body-1">
                    <strong>Connecting f, f', and f'':</strong>
                    <ul class="pl-4 mt-1">
                      <li>$f'(x)$ → slope and rate of change of $f(x)$</li>
                      <li>$f''(x)$ → rate of change of $f'(x)$ and concavity of $f(x)$</li>
                      <li>Zeros of $f'$ → horizontal tangents; zeros of $f''$ → potential inflection points</li>
                    </ul>
                    <br>
                    <strong>Optimization Strategy:</strong>
                    <ol class="pl-4 mt-1">
                      <li>Identify objective function and constraints</li>
                      <li>Use constraints to express objective as function of one variable</li>
                      <li>Find critical points and test for extrema</li>
                      <li>Check endpoints if on closed interval</li>
                    </ol>
                    <br>
                    <strong>Implicit Relations:</strong> Use implicit differentiation to find $\frac{dy}{dx}$ and $\frac{d^2y}{dx^2}$ for curves not explicitly solved for $y$, enabling analysis of tangent lines and concavity.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <h2 class="text-h5 font-weight-medium mb-3">Key Tests & Theorems 📝</h2>
              <v-row>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">Core Theorems:</h3>
                  <ul class="pl-5 text-body-2">
                    <li><strong>MVT:</strong> If $f$ cont. on $[a,b]$, diff. on $(a,b)$, then $f'(c) = \frac{f(b)-f(a)}{b-a}$ for some $c$</li>
                    <li><strong>EVT:</strong> If $f$ cont. on $[a,b]$, then $f$ has absolute max & min</li>
                  </ul>
                  <h3 class="text-h6 mb-2 mt-3">Function Behavior:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>$f'(x)>0$ ⟹ $f$ increasing</li>
                    <li>$f'(x)<0$ ⟹ $f$ decreasing</li>
                    <li>$f''(x)>0$ ⟹ $f$ concave up</li>
                    <li>$f''(x)<0$ ⟹ $f$ concave down</li>
                  </ul>
                  <h3 class="text-h6 mb-2 mt-3">Finding Extrema:</h3>
                  <ul class="pl-5 text-body-2">
                    <li><strong>Critical points:</strong> $f'(c) = 0$ or undefined</li>
                    <li><strong>Candidates Test:</strong> Check critical points + endpoints</li>
                  </ul>
                </v-col>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">Derivative Tests:</h3>
                  <ul class="pl-5 text-body-2">
                    <li><strong>1st Derivative Test:</strong> Sign change of $f'$ around critical point</li>
                    <li><strong>2nd Derivative Test:</strong> $f''(c)>0$ ⟹ min, $f''(c)<0$ ⟹ max</li>
                  </ul>
                  <h3 class="text-h6 mb-2 mt-3">Optimization Steps:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>1. Identify objective function & constraints</li>
                    <li>2. Express as function of one variable</li>
                    <li>3. Find critical points & test for extrema</li>
                    <li>4. Check endpoints if applicable</li>
                  </ul>
                  <h3 class="text-h6 mb-2 mt-3">Key Relationships:</h3>
                  <ul class="pl-5 text-body-2">
                    <li>$f'$ zeros ⟹ horizontal tangents on $f$</li>
                    <li>$f''$ zeros ⟹ potential inflection points</li>
                    <li>Inflection point: concavity changes</li>
                  </ul>
                </v-col>
              </v-row>
            </section>

            <v-divider class="my-5"></v-divider>

            <section>
              <h2 class="text-h5 font-weight-medium mb-3">Example: Solving an Optimization Problem 🎯</h2>
              <p class="text-body-1">
                A farmer wants to fence an area of 1.5 million square feet in a rectangular field and then divide it in half with a fence parallel to one of the sides of the rectangle. What should the lengths of the sides of the rectangular field be so as to minimize the cost of the fence (i.e., minimize the total length of fencing used)?
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 1: Understand & Diagram</strong>
                Let the rectangle have length $L$ and width $W$. The dividing fence is parallel to the side of length $W$.
                The area is $A = LW = 1,500,000 \text{ ft}^2$.
                The total length of fencing is $F = 2L + 3W$. We want to minimize $F$.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 2: Objective Function & Constraint</strong>
                Objective: Minimize $F = 2L + 3W$.
                Constraint: $LW = 1,500,000$.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 3: Express as a Function of One Variable</strong>
                From the constraint, $L = \frac{1,500,000}{W}$.
                Substitute into $F$: $F(W) = 2\left(\frac{1,500,000}{W}\right) + 3W = \frac{3,000,000}{W} + 3W$.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 4: Determine the Domain</strong>
                Since $W$ is a length, $W > 0$. There's no upper bound from the problem statement.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 5: Use Calculus to Find Minimum</strong>
                Find the derivative of $F(W)$:
                $$F'(W) = \frac{d}{dW}\left(3,000,000 W^{-1} + 3W\right) = -3,000,000 W^{-2} + 3 = -\frac{3,000,000}{W^2} + 3$$
                Set $F'(W) = 0$ to find critical points:
                $$-\frac{3,000,000}{W^2} + 3 = 0 \Rightarrow 3 = \frac{3,000,000}{W^2} \Rightarrow W^2 = \frac{3,000,000}{3} = 1,000,000$$
                $$W = \sqrt{1,000,000} = 1000 \text{ ft (since } W>0)$$
                To confirm it's a minimum, use the Second Derivative Test:
                $$F''(W) = \frac{d}{dW}\left(-3,000,000 W^{-2} + 3\right) = 6,000,000 W^{-3} = \frac{6,000,000}{W^3}$$
                At $W=1000$: $F''(1000) = \frac{6,000,000}{(1000)^3} = \frac{6,000,000}{1,000,000,000} > 0$.
                Since $F''(1000) > 0$, this confirms a local minimum at $W=1000$. As it's the only critical point in the domain $(0, \infty)$, this corresponds to an absolute minimum.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 6: Find Dimensions and Answer</strong>
                When $W = 1000$ ft:
                $$L = \frac{1,500,000}{1000} = 1500 \text{ ft}$$
                The dimensions that minimize the fence are $1500 \text{ ft by } 1000 \text{ ft}$.
                The minimum fence length would be $F = 2(1500) + 3(1000) = 3000 + 3000 = 6000 \text{ ft}$.
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