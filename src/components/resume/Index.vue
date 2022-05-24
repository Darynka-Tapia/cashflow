<template>
  <main>
    <p>{{ labelVisual }}</p>
    <h1>{{ amountCurrency }}</h1>
    <div class="graphic">
      <slot name="graphic"></slot>
    </div>
    <div class="action">
      <slot name="action"></slot>
    </div>
  </main>
</template>

<script>
const currencyFormatter = new Intl.NumberFormat("es-MX", {
  style: "currency",
  currency: "MXN",
});
export default {
  props: {
    label: {
      type: String,
      default: null,
    },
    dateLabel: { type: String },
    amount: {
      type: Number,
      default: null,
    },
    totalAmount: { type: Number },
  },
  computed: {
    amountVisual() {
      return this.amount !== null ? this.amount : this.totalAmount;
    },
    labelVisual() {
      return this.label !== null ? this.label : this.dateLabel;
    },
    amountCurrency() {
      return currencyFormatter.format(this.amountVisual);
    },
  },
};
</script>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-content: center;
  flex-direction: column;
  width: 100%;
  margin-top: 30px;
}
h1,
p {
  margin: 0;
  text-align: center;
}
h1 {
  color: var(--brand-green);
}
.graphic,
.action {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding: 48px 24px;
  box-sizing: border-box;
}
</style>
