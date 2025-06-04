<template>
  <v-container class="pa-0 bg-grey-lighten-4" style="min-height: 100vh;" fluid>
    <v-row justify="center" align="start" style="min-height: inherit;" class="py-md-6">
      <v-col cols="12" md="11" lg="9" xl="8">
        <v-card elevation="4" rounded="xl" class="pa-5 pa-md-8">
          <v-card-title class="text-h4 font-weight-bold mb-2 text-primary">Unit 7: Differential Equations</v-card-title>
          <v-card-text>
            <p class="text-body-1 mb-4">
              Welcome to Unit 7: <strong>Differential Equations</strong>! This unit explores equations that involve an unknown function and one or more of its derivatives. You'll learn how to model real-world phenomena involving rates of change, such as population growth, radioactive decay, and motion. We will visualize solutions using <strong>slope fields</strong>, approximate solutions numerically with <strong>Euler's method</strong>, and find exact solutions for certain types of differential equations using techniques like <strong>separation of variables</strong>. We'll also investigate common and important models like <strong>exponential</strong> and <strong>logistic growth</strong>.
            </p>

            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="light-green-darken-3" class="mr-3 mt-1">mdi-shape-plus</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Modeling and Verifying Differential Equations</h2>
                  <div class="text-body-1">
                    <h3 class="text-subtitle-1 font-weight-medium mt-3 mb-2">Creating Mathematical Models</h3>
                    Many real-world phenomena can be described by the relationship between a quantity and its rate of change. <strong>Modeling with differential equations</strong> involves translating these verbal descriptions into mathematical equations. For example, "the rate of population growth is proportional to the current population" can be written as $\frac{dP}{dt} = kP$.
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-4 mb-2">Verifying Solutions</h3>
                    To <strong>verify if a given function is a solution</strong> to a differential equation, substitute the function and its derivatives into the differential equation. If the substitution results in a true statement (i.e., both sides of the equation are equal), then the function is a solution. For example, to verify if $y=e^{2x}$ is a solution to $\frac{dy}{dx} = 2y$, find $\frac{dy}{dx} = 2e^{2x}$ and substitute: $2e^{2x} = 2(e^{2x})$, which is true.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="blue-grey-darken-1" class="mr-3 mt-1">mdi-chart-scatter-plot</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Slope Fields and Visual Analysis</h2>
                  <div class="text-body-1">
                    <h3 class="text-subtitle-1 font-weight-medium mt-3 mb-2">Understanding Slope Fields</h3>
                    A <strong>slope field</strong> (or direction field) is a graphical representation of a first-order differential equation of the form $\frac{dy}{dx} = f(x,y)$. At various points $(x,y)$ in the plane, short line segments are drawn with slope equal to $f(x,y)$. This provides a visualization of the direction solutions to the differential equation take at each point.
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-4 mb-2">Using Slope Fields for Analysis</h3>
                    Slope fields allow us to understand the behavior of solutions without explicitly solving the differential equation. By observing the flow of the line segments, we can:
                    <ul class="pl-4 mt-1">
                      <li>Sketch approximate solution curves that pass through a given point</li>
                      <li>Identify equilibrium solutions (where slopes are zero)</li>
                      <li>Analyze the long-term behavior of solutions (e.g., do they approach a certain value, increase without bound, etc.?)</li>
                    </ul>
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="indigo-accent-3" class="mr-3 mt-1">mdi-calculator-variant</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Euler's Method for Numerical Solutions</h2>
                  <div class="text-body-1">
                    <strong>Euler's Method</strong> is a numerical procedure for approximating the solution of a differential equation $\frac{dy}{dx} = f(x,y)$ with a given initial condition $y(x_0) = y_0$. It uses tangent line approximations iteratively:
                    $$y_{n+1} = y_n + h \cdot f(x_n, y_n)$$
                    where $h$ is the step size, $x_{n+1} = x_n + h$, and $(x_n, y_n)$ is the current point. Smaller step sizes generally lead to better approximations.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="purple-darken-3" class="mr-3 mt-1">mdi-ungroup</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Solving with Separation of Variables</h2>
                  <div class="text-body-1">
                    <h3 class="text-subtitle-1 font-weight-medium mt-3 mb-2">General Solutions</h3>
                    <strong>Separation of variables</strong> is a technique for solving first-order differential equations that can be written in the form $\frac{dy}{dx} = g(x)h(y)$. The method involves:
                    <ol class="pl-4 mt-1">
                      <li>Separating variables: $\frac{1}{h(y)} dy = g(x) dx$</li>
                      <li>Integrating both sides: $\int \frac{1}{h(y)} dy = \int g(x) dx$</li>
                      <li>Solving for $y$ if possible, including the constant of integration $C$. This gives the <strong>general solution</strong></li>
                    </ol>
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-4 mb-2">Particular Solutions with Initial Conditions</h3>
                    A <strong>particular solution</strong> is found by using an initial condition (e.g., $y(x_0) = y_0$) to determine the specific value of the constant of integration $C$ in the general solution obtained through separation of variables. This yields a unique solution curve that passes through the given point.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="amber-darken-2" class="mr-3 mt-1">mdi-chart-bell-curve</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Exponential and Logistic Growth Models</h2>
                  <div class="text-body-1">
                    <h3 class="text-subtitle-1 font-weight-medium mt-3 mb-2">Exponential Models</h3>
                    Differential equations of the form $\frac{dy}{dt} = ky$ model situations where the rate of change of a quantity $y$ is directly proportional to $y$ itself. This leads to <strong>exponential growth</strong> (if $k>0$) or <strong>exponential decay</strong> (if $k<0$). The general solution is:
                    $$y(t) = y_0 e^{kt}$$
                    where $y_0$ is the initial quantity at $t=0$. Examples include population growth, radioactive decay, and compound interest.
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-4 mb-2">Logistic Models</h3>
                    <strong>Logistic models</strong> describe growth that is initially exponential but slows down as it approaches a carrying capacity $L$. The differential equation is often written as:
                    $$\frac{dP}{dt} = kP\left(1 - \frac{P}{L}\right) \quad \text{or} \quad \frac{dP}{dt} = \frac{k}{L}P(L-P)$$
                    The solution (logistic function) produces an S-shaped curve:
                    $$P(t) = \frac{L}{1 + Ae^{-kt}}$$
                    where $A = \frac{L-P_0}{P_0}$. The population $P(t)$ approaches the carrying capacity $L$ as $t \to \infty$. The growth rate is fastest when $P = L/2$.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <h2 class="text-h5 font-weight-medium mb-3">Key Concepts & Formulas 🔑</h2>
              <v-row>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">📊 Basic Concepts:</h3>
                  <ul class="pl-5 text-body-2">
                    <li><strong>Differential Equation:</strong> Equation involving unknown function and its derivatives</li>
                    <li><strong>Slope Field:</strong> Graphical representation of $\frac{dy}{dx} = f(x,y)$</li>
                    <li><strong>Solution Verification:</strong> Substitute function into DE</li>
                  </ul>
                  
                  <h3 class="text-h6 mb-2 mt-3">🔧 Solution Methods:</h3>
                  <ul class="pl-5 text-body-2">
                    <li><strong>Euler's Method:</strong> $y_{n+1} = y_n + h \cdot f(x_n, y_n)$</li>
                    <li><strong>Separation of Variables:</strong> $\int \frac{1}{h(y)}dy = \int g(x)dx$</li>
                  </ul>
                </v-col>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">📈 Growth Models:</h3>
                  <ul class="pl-5 text-body-2">
                    <li><strong>Exponential:</strong> $\frac{dy}{dt} = ky$ → $y(t) = y_0 e^{kt}$</li>
                    <li><strong>Logistic:</strong> $\frac{dP}{dt} = kP(1 - \frac{P}{L})$ → $P(t) = \frac{L}{1 + Ae^{-kt}}$</li>
                  </ul>
                  
                  <h3 class="text-h6 mb-2 mt-3">🎯 Key Properties:</h3>
                  <ul class="pl-5 text-body-2">
                    <li><strong>General Solution:</strong> Contains arbitrary constant $C$</li>
                    <li><strong>Particular Solution:</strong> Uses initial condition to find $C$</li>
                    <li><strong>Carrying Capacity:</strong> Limit $L$ in logistic growth</li>
                  </ul>
                </v-col>
              </v-row>
            </section>

            <v-divider class="my-5"></v-divider>

            <section>
              <h2 class="text-h5 font-weight-medium mb-3">Example: Solving a Separable Differential Equation 🧩</h2>
              <p class="text-body-1">
                Find the particular solution to the differential equation $\frac{dy}{dx} = 2xy^2$ given the initial condition $y(1) = \frac{1}{2}$.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 1: Separate Variables</strong>
                If $y \neq 0$, we can write:
                $$\frac{1}{y^2} dy = 2x \, dx$$
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 2: Integrate Both Sides</strong>
                $$\int y^{-2} dy = \int 2x \, dx$$
                $$-y^{-1} = x^2 + C$$
                $$-\frac{1}{y} = x^2 + C$$
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 3: Apply the Initial Condition</strong>
                Use $y(1) = \frac{1}{2}$, so when $x=1$, $y=\frac{1}{2}$:
                $$-\frac{1}{1/2} = (1)^2 + C$$
                $$-2 = 1 + C$$
                $$C = -2 - 1 = -3$$
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 4: Substitute C and Solve for y</strong>
                Substitute $C=-3$ into the general solution:
                $$-\frac{1}{y} = x^2 - 3$$
                Multiply by -1:
                $$\frac{1}{y} = 3 - x^2$$
                Take the reciprocal of both sides:
                $$y = \frac{1}{3 - x^2}$$
                This is the particular solution.
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