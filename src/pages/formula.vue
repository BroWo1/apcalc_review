<template>
  <v-container class="pa-0 bg-grey-lighten-4" style="min-height: 100vh;" fluid>
    <v-row justify="center" align="start" style="min-height: inherit;" class="py-md-6">
      <v-col cols="12" md="11" lg="9" xl="8">
        <v-card elevation="4" rounded="xl" class="pa-5 pa-md-8">
          <v-card-title class="text-h4 font-weight-bold mb-6 text-primary">AP Calculus Formula Sheet</v-card-title>
          <v-card-text>

            <!-- Limits Section -->
            <section class="mb-8">
              <h2 class="text-h5 font-weight-medium mb-3 text-grey-darken-3">Limits</h2>
              <v-list density="compact" lines="two">
                <v-list-item>
                  <v-list-item-title class="font-weight-medium">Basic Limit Properties</v-list-item-title>
                  <v-list-item-subtitle>If $\lim_{x \to c} f(x) = L$ and $\lim_{x \to c} g(x) = M$:
                    <ul class="pl-5 mt-1">
                      <li>Sum/Difference: $\lim_{x \to c} [f(x) \pm g(x)] = L \pm M$</li>
                      <li>Constant Multiple: $\lim_{x \to c} [k \cdot f(x)] = kL$</li>
                      <li>Product: $\lim_{x \to c} [f(x)g(x)] = LM$</li>
                      <li>Quotient: $\lim_{x \to c} \frac{f(x)}{g(x)} = \frac{L}{M}$, provided $M \neq 0$</li>
                      <li>Power: $\lim_{x \to c} [f(x)]^n = L^n$</li>
                    </ul>
                  </v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="mt-2">
                  <v-list-item-title class="font-weight-medium">Special Trigonometric Limits</v-list-item-title>
                  <v-list-item-subtitle>
                    <ul class="pl-5 mt-1">
                      <li>$\lim_{x \to 0} \frac{\sin x}{x} = 1$</li>
                      <li>$\lim_{x \to 0} \frac{1 - \cos x}{x} = 0$</li>
                    </ul>
                  </v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="mt-2">
                  <v-list-item-title class="font-weight-medium">Definition of $e$</v-list-item-title>
                  <v-list-item-subtitle>
                    <ul class="pl-5 mt-1">
                      <li>$\lim_{x \to \infty} (1 + \frac{1}{x})^x = e$</li>
                       <li>$\lim_{n \to 0} (1 + n)^{1/n} = e$</li>
                    </ul>
                  </v-list-item-subtitle>
                </v-list-item>
              </v-list>
            </section>

            <v-divider class="my-6"></v-divider>

            <!-- Derivatives Section -->
            <section class="mb-8">
              <h2 class="text-h5 font-weight-medium mb-3 text-grey-darken-3">Derivatives</h2>
              <v-list density="compact" lines="two">
                <v-list-item>
                  <v-list-item-title class="font-weight-medium">Definition of the Derivative</v-list-item-title>
                  <v-list-item-subtitle>$f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$ or $f'(a) = \lim_{x \to a} \frac{f(x) - f(a)}{x-a}$</v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="mt-2">
                  <v-list-item-title class="font-weight-medium">Basic Differentiation Rules</v-list-item-title>
                  <v-list-item-subtitle>
                    <ul class="pl-5 mt-1">
                      <li>Constant Rule: $\frac{d}{dx}[c] = 0$</li>
                      <li>Power Rule: $\frac{d}{dx}[x^n] = nx^{n-1}$</li>
                      <li>Constant Multiple: $\frac{d}{dx}[cf(x)] = cf'(x)$</li>
                      <li>Sum/Difference: $\frac{d}{dx}[f(x) \pm g(x)] = f'(x) \pm g'(x)$</li>
                      <li>Product Rule: $\frac{d}{dx}[f(x)g(x)] = f'(x)g(x) + f(x)g'(x)$</li>
                      <li>Quotient Rule: $\frac{d}{dx}\left[\frac{f(x)}{g(x)}\right] = \frac{f'(x)g(x) - f(x)g'(x)}{[g(x)]^2}$</li>
                    </ul>
                  </v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="mt-2">
                  <v-list-item-title class="font-weight-medium">Chain Rule</v-list-item-title>
                  <v-list-item-subtitle>If $h(x) = f(g(x))$, then $h'(x) = f'(g(x)) \cdot g'(x)$. Or $\frac{dy}{dx} = \frac{dy}{du} \cdot \frac{du}{dx}$.</v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="mt-2">
                  <v-list-item-title class="font-weight-medium">Common Derivatives</v-list-item-title>
                  <v-list-item-subtitle>
                    <v-row>
                      <v-col cols="12" sm="6">
                        <ul class="pl-5 mt-1">
                          <li>$\frac{d}{dx}[e^x] = e^x$</li>
                          <li>$\frac{d}{dx}[a^x] = a^x \ln a$</li>
                          <li>$\frac{d}{dx}[\ln x] = \frac{1}{x}$</li>
                          <li>$\frac{d}{dx}[\log_a x] = \frac{1}{x \ln a}$</li>
                          <li>$\frac{d}{dx}[\sin x] = \cos x$</li>
                          <li>$\frac{d}{dx}[\cos x] = -\sin x$</li>
                          <li>$\frac{d}{dx}[\tan x] = \sec^2 x$</li>
                        </ul>
                      </v-col>
                      <v-col cols="12" sm="6">
                        <ul class="pl-5 mt-1">
                          <li>$\frac{d}{dx}[\csc x] = -\csc x \cot x$</li>
                          <li>$\frac{d}{dx}[\sec x] = \sec x \tan x$</li>
                          <li>$\frac{d}{dx}[\cot x] = -\csc^2 x$</li>
                          <li>$\frac{d}{dx}[\arcsin x] = \frac{1}{\sqrt{1-x^2}}$</li>
                          <li>$\frac{d}{dx}[\arctan x] = \frac{1}{1+x^2}$</li>
                          <li>$\frac{d}{dx}[\text{arcsec } x] = \frac{1}{|x|\sqrt{x^2-1}}$</li>
                        </ul>
                      </v-col>
                    </v-row>
                  </v-list-item-subtitle>
                </v-list-item>
                 <v-list-item  class="mt-2">
                  <v-list-item-title class="font-weight-medium">L'Hôpital's Rule</v-list-item-title>
                  <v-list-item-subtitle>If $\lim_{x \to c} \frac{f(x)}{g(x)}$ is of the form $\frac{0}{0}$ or $\frac{\infty}{\infty}$, then $\lim_{x \to c} \frac{f(x)}{g(x)} = \lim_{x \to c} \frac{f'(x)}{g'(x)}$, provided the latter limit exists.</v-list-item-subtitle>
                </v-list-item>
              </v-list>
            </section>

            <v-divider class="my-6"></v-divider>

            <!-- Integrals Section -->
            <section class="mb-8" lines="two">
              <h2 class="text-h5 font-weight-medium mb-3 text-grey-darken-3">Integrals</h2>
              <v-list density="compact">
                <v-list-item>
                  <v-list-item-title class="font-weight-medium">Definition of Definite Integral</v-list-item-title>
                  <v-list-item-subtitle>$\int_a^b f(x) dx = \lim_{n \to \infty} \sum_{i=1}^n f(x_i^*) \Delta x$</v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="mt-2">
                  <v-list-item-title class="font-weight-medium">Fundamental Theorem of Calculus</v-list-item-title>
                  <v-list-item-subtitle>
                    <ul class="pl-5 mt-1">
                      <li>Part 1: If $F(x) = \int_a^x f(t) dt$, then $F'(x) = f(x)$.</li>
                      <li>Part 2: $\int_a^b f(x) dx = F(b) - F(a)$, where $F$ is any antiderivative of $f$.</li>
                    </ul>
                  </v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="mt-2">
                  <v-list-item-title class="font-weight-medium">Basic Integration Rules</v-list-item-title>
                  <v-list-item-subtitle>
                    <ul class="pl-5 mt-1">
                      <li>$\int k \, dx = kx + C$</li>
                      <li>$\int x^n \, dx = \frac{x^{n+1}}{n+1} + C \quad (n \neq -1)$</li>
                      <li>$\int \frac{1}{x} \, dx = \ln|x| + C$</li>
                      <li>$\int e^x \, dx = e^x + C$</li>
                      <li>$\int a^x \, dx = \frac{a^x}{\ln a} + C$</li>
                      <li>$\int \sin x \, dx = -\cos x + C$</li>
                      <li>$\int \cos x \, dx = \sin x + C$</li>
                      <li>$\int \sec^2 x \, dx = \tan x + C$</li>
                      <li>$\int \csc^2 x \, dx = -\cot x + C$</li>
                      <li>$\int \sec x \tan x \, dx = \sec x + C$</li>
                      <li>$\int \csc x \cot x \, dx = -\csc x + C$</li>
                      <li>$\int \frac{1}{\sqrt{a^2-x^2}} \, dx = \arcsin(\frac{x}{a}) + C$</li>
                      <li>$\int \frac{1}{a^2+x^2} \, dx = \frac{1}{a}\arctan(\frac{x}{a}) + C$</li>
                    </ul>
                  </v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="mt-2">
                  <v-list-item-title class="font-weight-medium">Integration by Substitution (u-substitution)</v-list-item-title>
                  <v-list-item-subtitle>$\int f(g(x))g'(x) \, dx = \int f(u) \, du$, where $u = g(x)$.</v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="mt-2">
                  <v-list-item-title class="font-weight-medium">Integration by Parts</v-list-item-title>
                  <v-list-item-subtitle>$\int u \, dv = uv - \int v \, du$</v-list-item-subtitle>
                </v-list-item>
              </v-list>
            </section>

            <v-divider class="my-6"></v-divider>

            <!-- Applications Section -->
            <section>
              <h2 class="text-h5 font-weight-medium mb-3 text-grey-darken-3">Applications</h2>
              <v-list density="compact" lines="two">
                <v-list-item>
                  <v-list-item-title class="font-weight-medium">Mean Value Theorem</v-list-item-title>
                  <v-list-item-subtitle>If $f$ is continuous on $[a,b]$ and differentiable on $(a,b)$, then there exists $c \in (a,b)$ such that $f'(c) = \frac{f(b)-f(a)}{b-a}$.</v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="mt-2">
                  <v-list-item-title class="font-weight-medium">Average Value of a Function</v-list-item-title>
                  <v-list-item-subtitle>$f_{avg} = \frac{1}{b-a} \int_a^b f(x) \, dx$</v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="mt-2">
                  <v-list-item-title class="font-weight-medium">Area Between Curves</v-list-item-title>
                  <v-list-item-subtitle>If $f(x) \ge g(x)$ on $[a,b]$: $A = \int_a^b [f(x) - g(x)] \, dx$. <br>If $f(y) \ge g(y)$ on $[c,d]$: $A = \int_c^d [f(y) - g(y)] \, dy$.</v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="mt-2">
                  <v-list-item-title class="font-weight-medium">Volume by Disks</v-list-item-title>
                  <v-list-item-subtitle>Rotation about x-axis: $V = \pi \int_a^b [R(x)]^2 \, dx$. <br>Rotation about y-axis: $V = \pi \int_c^d [R(y)]^2 \, dy$.</v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="mt-2">
                  <v-list-item-title class="font-weight-medium">Volume by Washers</v-list-item-title>
                  <v-list-item-subtitle>Rotation about x-axis: $V = \pi \int_a^b ([R(x)]^2 - [r(x)]^2) \, dx$. <br>Rotation about y-axis: $V = \pi \int_c^d ([R(y)]^2 - [r(y)]^2) \, dy$.</v-list-item-subtitle>
                </v-list-item>
              </v-list>
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
    await nextTick();
    if (typeof window.MathJax.typesetPromise === 'function') {
      window.MathJax.typesetPromise();
    } else if (window.MathJax.Hub && typeof window.MathJax.Hub.Queue === 'function') {
      window.MathJax.Hub.Queue(["Typeset", window.MathJax.Hub]);
    }
  }
});
</script>

<style scoped>
.v-card {
  background-color: #fdfdfd;
}

section {
  padding: 10px 0;
}

ul {
  list-style-type: disc; /* More standard bullet points */
}

.v-list-item-subtitle ul li {
  margin-bottom: 4px; /* Spacing between formula list items */
}

p, li, .v-list-item-subtitle {
  line-height: 1.7;
}

.v-list-item-title {
  color: #333; /* Darker title for better contrast */
}
</style>