<template>
  <Suspense>
    <template #default>
      <Home />
    </template>
    <template #fallback>
      <SplashScreen />
    </template>
  </Suspense>
</template>
<script>
import SplashScreen from "@/components/SplashScreen.vue";
import { defineAsyncComponent } from "vue";

export default {
  components: {
    SplashScreen,
    Home: defineAsyncComponent(
      () =>
        new Promise((resolve) => {
          setTimeout(() => {
            resolve(import("./components/Home.vue"));
          }, 500);
        })
    ),
  },
};
</script>

<style>
html,
body,
.app {
  padding: 0px;
  margin: 0px;
  min-height: 100vh;
}
:root {
  --brand-green: #04b500;
  --brand-blue: #0689b0;
}
</style>
