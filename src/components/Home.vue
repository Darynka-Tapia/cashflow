<template>
  <Layout>
    <template #header>
      <Header></Header>
    </template>
    <template #resume>
      <Resume
        :label="label"
        date-label="2020-10-05"
        :amount="amount"
        :total-amount="totalAmount"
      >
        <template #graphic>
          <Graphic :amounts="amounts" @select="select" @unselect="unselect" />
        </template>
        <template #action><Action @create="create" /></template>
      </Resume>
    </template>
    <template #movements>
      <Movements :movements="movements" @remove="remove"></Movements>
    </template>
  </Layout>
</template>

<script>
import Layout from "./Layout.vue";
import Header from "./Header.vue";
import Resume from "./resume/Index.vue";
import Graphic from "./resume/Graphic.vue";
import Action from "./Actions.vue";
import Movements from "./movements/Index.vue";

export default {
  components: {
    Layout,
    Header,
    Resume,
    Action,
    Movements,
    Graphic,
  },
  data() {
    return {
      label: "Ahorro Total", // "",
      amount: null, // 10000,
      movements: [],
      isUnselect: false,
    };
  },
  mounted() {
    const movements = JSON.parse(localStorage.getItem("movements"));
    if (Array.isArray(movements)) {
      this.movements = movements.map((m) => {
        return { ...m, time: new Date(m.time) };
      });
    }
  },
  methods: {
    create(data) {
      this.movements.push(data);
      this.save();
    },
    remove(id) {
      this.movements.splice(id, 1);
      this.save();
    },
    save() {
      localStorage.setItem("movements", JSON.stringify(this.movements));
    },
    select(amount) {
      this.amount = amount;
    },
    unselect() {
      this.amount = null;
    },
  },
  computed: {
    amounts() {
      const lastDays = this.movements
        .filter((m) => {
          const today = new Date();
          const oldDate = today.setDate(today.getDate() - 30);
          return m.time > oldDate;
        })
        .map((m) => m.amount);

      return lastDays.map((m, i) => {
        const lastMovements = lastDays.slice(0, i + 1);
        return lastMovements.reduce((suma, movement) => {
          return suma + movement;
        }, 0);
      });
    },
    totalAmount() {
      const result = this.movements.reduce((suma, m) => {
        return suma + m.amount;
      }, 0);
      return result;
    },
  },
};
</script>
