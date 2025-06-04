<template>
  <v-container class="pa-0 bg-grey-lighten-4" style="min-height: 100vh;" fluid>
    <v-row justify="center" align="start" style="min-height: inherit;" class="py-md-6">
      <v-col cols="12" md="11" lg="9" xl="8">
        <v-card elevation="4" rounded="xl" class="pa-5 pa-md-8">
          <v-card-title class="text-h4 font-weight-bold mb-2 text-primary">Unit 8: Applications of Integration</v-card-title>
          <v-card-text>
            <p class="text-body-1 mb-4">
              Unit 8 showcases the diverse applications of integration in solving real-world and theoretical problems. Building on the fundamentals of integration from <strong>Unit 6</strong>, this unit explores how to calculate the <strong>average value of a function</strong>, analyze <strong>motion by connecting position, velocity, and acceleration</strong>, determine <strong>accumulated change in various contexts</strong>, and compute geometric quantities such as <strong>areas between curves</strong>, <strong>volumes of solids</strong> (using cross-sections, discs, and washers), and the <strong>length of curves</strong>. These powerful tools extend the reach of calculus into various fields of science, engineering, economics, and mathematics.
            </p>

            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="green-darken-4" class="mr-3 mt-1">mdi-chart-histogram</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Average Value, Motion, and Accumulation Applications</h2>
                  <div class="text-body-1">
                    <h3 class="text-subtitle-1 font-weight-medium mt-3 mb-2">Average Value of a Function</h3>
                    The <strong>average value</strong> of a continuous function $f(x)$ on an interval $[a,b]$ is:
                    $$f_{avg} = \frac{1}{b-a} \int_a^b f(x) dx$$
                    Geometrically, this represents the height of a rectangle with base $(b-a)$ that has the same area as the area under the curve.
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-4 mb-2">Motion Analysis with Integration</h3>
                    Integration reverses differentiation in kinematics:
                    <ul class="pl-4 mt-1">
                      <li><strong>Displacement</strong> from $t_1$ to $t_2$: $\Delta s = \int_{t_1}^{t_2} v(t) dt$</li>
                      <li><strong>Total distance traveled</strong>: $\int_{t_1}^{t_2} |v(t)| dt$</li>
                      <li><strong>Change in velocity</strong>: $\Delta v = \int_{t_1}^{t_2} a(t) dt$</li>
                      <li>Position: $s(t) = s(t_0) + \int_{t_0}^t v(x) dx$</li>
                    </ul>
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-4 mb-2">Accumulation Functions in Applied Contexts</h3>
                    If $R(t)$ represents a rate of change, then $\int_a^b R(t) dt$ gives the <strong>total accumulation</strong> from $t=a$ to $t=b$. Applications include flow rates, population growth, and emission rates.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="red-darken-4" class="mr-3 mt-1">mdi-vector-rectangle</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Area Between Curves</h2>
                  <div class="text-body-1">
                    <h3 class="text-subtitle-1 font-weight-medium mt-3 mb-2">Functions of x</h3>
                    For $f(x) \ge g(x)$ on $[a,b]$:
                    $$A = \int_a^b [f(x) - g(x)] dx \quad \text{(Top - Bottom)}$$
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-4 mb-2">Functions of y</h3>
                    For $f(y) \ge g(y)$ on $[c,d]$ (where $f(y)$ is rightmost):
                    $$A = \int_c^d [f(y) - g(y)] dy \quad \text{(Right - Left)}$$
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-4 mb-2">Multiple Intersections</h3>
                    When curves intersect multiple times or the top/right function changes, split the integral into parts where one function consistently remains above (or to the right of) the other. Sum the areas of these sub-regions.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="teal-darken-4" class="mr-3 mt-1">mdi-cube-outline</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Volume by Cross-Sections</h2>
                  <div class="text-body-1">
                    For a solid with cross-sectional area $A(x)$ perpendicular to the x-axis: $V = \int_a^b A(x) dx$
                    <br>For cross-sections perpendicular to the y-axis: $V = \int_c^d A(y) dy$
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-3 mb-2">Common Cross-Section Shapes</h3>
                    <ul class="pl-4 mt-1">
                      <li><strong>Squares</strong> with side $s$: $A = s^2$</li>
                      <li><strong>Rectangles</strong> with sides $s_1, s_2$: $A = s_1 s_2$</li>
                      <li><strong>Triangles</strong> with base $b$ and height $h$: $A = \frac{1}{2}bh$</li>
                      <li><strong>Semicircles</strong> with radius $r$: $A = \frac{1}{2}\pi r^2$</li>
                    </ul>
                    The dimensions are typically functions of $x$ or $y$, determined by the base region.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="pink-darken-3" class="mr-3 mt-1">mdi-disc</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Volume by Disc Method</h2>
                  <div class="text-body-1">
                    Used when rotating a region around an axis creates circular disc cross-sections.
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-3 mb-2">Around Coordinate Axes</h3>
                    <ul class="pl-4 mt-1">
                      <li><strong>Around x-axis</strong>: $V = \pi \int_a^b [R(x)]^2 dx$</li>
                      <li><strong>Around y-axis</strong>: $V = \pi \int_c^d [R(y)]^2 dy$</li>
                    </ul>
                    where $R(x)$ or $R(y)$ is the radius (distance from axis to curve).
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-4 mb-2">Around Other Lines</h3>
                    <ul class="pl-4 mt-1">
                      <li><strong>Around $y=k$</strong>: $R(x) = |f(x) - k|$, so $V = \pi \int_a^b [f(x)-k]^2 dx$</li>
                      <li><strong>Around $x=h$</strong>: $R(y) = |g(y) - h|$, so $V = \pi \int_c^d [g(y)-h]^2 dy$</li>
                    </ul>
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="amber-darken-3" class="mr-3 mt-1">mdi-camera-iris</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Volume by Washer Method</h2>
                  <div class="text-body-1">
                    Used when the solid of revolution has a hole (region bounded by two functions), creating washer-shaped cross-sections.
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-3 mb-2">Around Coordinate Axes</h3>
                    <ul class="pl-4 mt-1">
                      <li><strong>Around x-axis</strong>: $V = \pi \int_a^b ([R(x)]^2 - [r(x)]^2) dx$</li>
                      <li><strong>Around y-axis</strong>: $V = \pi \int_c^d ([R(y)]^2 - [r(y)]^2) dy$</li>
                    </ul>
                    where $R$ is the outer radius and $r$ is the inner radius.
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-4 mb-2">Around Other Lines</h3>
                    Define outer and inner radii as distances from the axis of revolution to the respective boundaries. For rotation around $y=k$: $R(x) = |\text{outer curve}(x) - k|$ and $r(x) = |\text{inner curve}(x) - k|$.
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <div class="d-flex align-start">
                <v-icon color="blue-grey-darken-2" class="mr-3 mt-1">mdi-vector-curve</v-icon>
                <div class="flex-grow-1">
                  <h2 class="text-h5 font-weight-medium mb-2">Arc Length and Distance Traveled</h2>
                  <div class="text-body-1">
                    <h3 class="text-subtitle-1 font-weight-medium mt-3 mb-2">Smooth Planar Curves</h3>
                    <ul class="pl-4 mt-1">
                      <li><strong>Function $y=f(x)$</strong> from $x=a$ to $x=b$: $L = \int_a^b \sqrt{1 + [f'(x)]^2} \, dx$</li>
                      <li><strong>Function $x=g(y)$</strong> from $y=c$ to $y=d$: $L = \int_c^d \sqrt{1 + [g'(y)]^2} \, dy$</li>
                    </ul>
                    
                    <h3 class="text-subtitle-1 font-weight-medium mt-4 mb-2">Parametric Curves</h3>
                    For $x=x(t), y=y(t)$ from $t=\alpha$ to $t=\beta$:
                    $$L = \int_\alpha^\beta \sqrt{[x'(t)]^2 + [y'(t)]^2} \, dt$$
                  </div>
                </div>
              </div>
            </section>
            <v-divider class="my-5"></v-divider>

            <section class="mb-6">
              <h2 class="text-h5 font-weight-medium mb-3">Key Formulas & Applications 🛠️</h2>
              <v-row>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">📊 Basic Applications:</h3>
                  <ul class="pl-5 text-body-2">
                    <li><strong>Average Value:</strong> $f_{avg} = \frac{1}{b-a} \int_a^b f(x) dx$</li>
                    <li><strong>Displacement:</strong> $\int v(t) dt$</li>
                    <li><strong>Total Distance:</strong> $\int |v(t)| dt$</li>
                    <li><strong>Accumulation:</strong> $\int R(t) dt$</li>
                  </ul>
                  
                  <h3 class="text-h6 mb-2 mt-3">📐 Area & Cross-Sections:</h3>
                  <ul class="pl-5 text-body-2">
                    <li><strong>Area Between Curves:</strong> $\int [f(x) - g(x)] dx$</li>
                    <li><strong>Volume by Cross-Sections:</strong> $\int A(x) dx$</li>
                  </ul>
                </v-col>
                <v-col cols="12" md="6">
                  <h3 class="text-h6 mb-2">🔄 Solids of Revolution:</h3>
                  <ul class="pl-5 text-body-2">
                    <li><strong>Disc Method:</strong> $V = \pi \int [R(x)]^2 dx$</li>
                    <li><strong>Washer Method:</strong> $V = \pi \int ([R(x)]^2 - [r(x)]^2) dx$</li>
                  </ul>
                  
                  <h3 class="text-h6 mb-2 mt-3">📏 Arc Length:</h3>
                  <ul class="pl-5 text-body-2">
                    <li><strong>Function Form:</strong> $L = \int \sqrt{1 + [f'(x)]^2} \, dx$</li>
                    <li><strong>Parametric Form:</strong> $L = \int \sqrt{[x'(t)]^2 + [y'(t)]^2} \, dt$</li>
                  </ul>
                </v-col>
              </v-row>
            </section>

            <v-divider class="my-5"></v-divider>

            <section>
              <h2 class="text-h5 font-weight-medium mb-3">Example: Finding the Area Between Two Curves 📐</h2>
              <p class="text-body-1">
                Find the area of the region bounded by the curves $y = x^2$ and $y = x+2$.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 1: Find Intersection Points</strong>
                Set the functions equal: $x^2 = x+2 \Rightarrow x^2 - x - 2 = 0 \Rightarrow (x-2)(x+1) = 0$
                <br>Intersections at $x = -1$ and $x = 2$.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 2: Determine Top/Bottom Functions</strong>
                Test at $x=0$: $y = x^2$ gives $0$, $y = x+2$ gives $2$.
                <br>So $y = x+2$ is the top function on $[-1, 2]$.
              </p>
              <p class="text-body-1 mt-2">
                <strong>Step 3: Set Up and Evaluate</strong>
                $$A = \int_{-1}^{2} [(x+2) - x^2] dx = \int_{-1}^{2} (-x^2 + x + 2) dx$$
                $$= \left[ -\frac{x^3}{3} + \frac{x^2}{2} + 2x \right]_{-1}^{2} = \frac{9}{2} \text{ square units}$$
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