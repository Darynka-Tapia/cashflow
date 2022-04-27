<template>
  <div class="splashscreen">
    <img src="@/assets/cashflow-icon.svg" alt="logo" />
    <h1><span>Cash</span>Flow</h1>
  </div>
</template>

<style scoped>
.splashscreen {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
h1 {
  color: var(--brand-blue);
}
span {
  color: var(--brand-green);
}
</style>
