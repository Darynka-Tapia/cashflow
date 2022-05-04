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
        :total-amount="1000000"
      >
        <template #graphic><Graphic :amounts="amounts" /></template>
        <template #action><Action /></template>
      </Resume>
    </template>
    <template #movements>
      <Movements :movements="movements"></Movements>
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
      label: null, // "Ahorro Total",
      amount: null, // 10000,
      amounts: [100, 200, 500, 200, -400, -600, -300, 0, 300, 500],
      movements: [
        {
          id: 1,
          title: "Movimiento 1",
          description: `Recibi nomina Lorem Ipsum is simply dummy `,
          amount: 9000,
        },
        {
          id: 2,
          title: "Movimiento 2",
          description: `Compre en el super Lorem Ipsum is simply
            dummy text `,
          amount: -200,
        },
        {
          id: 3,
          title: "Movimiento 3",
          description: `Salida al cine por mi cumple 
            Lorem Ipsum is simply `,
          amount: -800,
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: `La descripcion del gasto Lorem Ipsum is simply dummy text
            of the printing `,
          amount: 100,
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: `La descripcion del gasto Lorem Ipsum is simply dummy text
            of the printing `,
          amount: 100,
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: `La descripcion del gasto Lorem Ipsum is simply dummy text
            of the printing `,
          amount: 100,
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: `La descripcion del gasto Lorem Ipsum is simply dummy text
            of the printing `,
          amount: 100,
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: `La descripcion del gasto Lorem Ipsum is simply dummy text
            of the printing `,
          amount: 100,
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: `La descripcion del gasto Lorem Ipsum is simply dummy text
            of the printing `,
          amount: 100,
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: `La descripcion del gasto Lorem Ipsum is simply dummy text
            of the printing `,
          amount: 100,
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: `La descripcion del gasto Lorem Ipsum is simply dummy text
            of the printing `,
          amount: 100,
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: `La descripcion del gasto Lorem Ipsum is simply dummy text
            of the printing `,
          amount: 100,
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: `La descripcion del gasto Lorem Ipsum is simply dummy text
            of the printing `,
          amount: 100,
        },
      ],
    };
  },
};
</script>
