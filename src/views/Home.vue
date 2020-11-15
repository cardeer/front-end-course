<template>
  <div class="layout">
    <div class="main">
      <Products />
      <Orders :total="getTotal" />
    </div>

    <!-- <v-calendar type="day"></v-calendar>
    <v-sparkline :value="[2, 10, 20, 0, 100]" :smooth="100" :line-width="1"></v-sparkline> -->
  </div>
</template>

<style scoped>
.main {
  display: flex;
  flex-grow: 1;
  max-height: 100vh;
}
</style>

<script>
import Orders from "@/components/Orders.vue";
import Products from "@/components/Products.vue";

export default {
  name: "Home",

  components: {
    Orders,
    Products,
  },

  data() {
    return {
      orderList: [
        // {
        //   name: "Lollipop",
        //   quantity: 1,
        //   pricePerUnit: 20,
        // },
      ],
    };
  },

  computed: {
    getTotal() {
      const total = this.$store.state.orderList.reduce(
        (prev, current) => prev + current.quantity * current.pricePerUnit,
        0
      );

      return new Intl.NumberFormat("th-TH", {
        style: "currency",
        currency: "THB",
      }).format(total);
    },
  },
};
</script>
