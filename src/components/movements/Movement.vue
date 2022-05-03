<template>
  <div class="movement">
    <div class="content">
      <h4 class="title">{{ title }}</h4>
      <p class="description">{{ description }}</p>
    </div>
    <div class="actions">
      <img
        class="delete"
        src="@/assets/trash-icon.svg"
        :alt="`id-${id}`"
        @click="remove"
      />
      <p :class="`amount ${statusAmount}`">{{ amountCurrency }}</p>
    </div>
  </div>
</template>

<script setup>
import { toRefs, defineProps, defineEmits, computed } from "vue";

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

const emit = defineEmits(["remove"]);
const remove = () => {
  emit("remove", id.value);
};
</script>

<style scoped>
.movement {
  background: #e6f9ff;
  border-radius: 15px;
  padding: 15px;
  display: flex;
  justify-content: space-between;
}
.title {
  margin: 0;
}
.description {
  margin: 0;
}
.actions {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: flex-end;
}
.amount {
  font-weight: 600;
}
.delete {
  width: 25px;
  height: 25px;
}
.amount.loss {
  color: red;
}
.amount.gain {
  color: green;
}
</style>
