<template>
  <div class="movement">
    <h3 class="title">{{ title }}</h3>
    <p class="description">{{ description }}</p>
    <div :class="`amount ${statusAmount}`">{{ amountCurrency }}</div>
    <div class="delete">
      <img src="@/assets/trash-icon.svg" :alt="`id-${id}`" />
    </div>
  </div>
</template>

<script setup>
import { toRefs, defineProps, computed } from "vue";

const props = defineProps({
  id: { type: Number },
  title: { type: String },
  description: { type: String },
  amount: { type: Number },
});

const { id, title, description, amount } = toRefs(props);

const statusAmount = computed(() => {
  return amount.value < 0 ? "loss" : "gain";
});

const currencyFormatter = new Intl.NumberFormat("es-MX", {
  style: "currency",
  currency: "MXN",
});
const amountCurrency = computed(() => {
  return currencyFormatter.format(amount.value);
});
</script>

<style scoped>
.movement {
  background: #e6f9ff;
  border-radius: 15px;
  padding: 15px;
  display: grid;
  grid-template-areas:
    "title title delete"
    "description description ."
    "description description amount";
}
.title {
  margin: 0;
  grid-area: title;
}
.description {
  margin: 0;
  grid-area: description;
}
.amount {
  grid-area: amount;
  font-weight: 600;
}
.delete {
  grid-area: delete;
  text-align: end;
}
.amount.loss {
  color: red;
}
.amount.gain {
  color: green;
}
</style>
