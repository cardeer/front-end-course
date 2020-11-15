<template>
  <div class="orders">
    <h2>Orders</h2>

    <div class="order-list">
      <div class="list" v-for="list in $store.state.orderList" :key="list.name">
        <p>{{ list.name }}</p>
        <p>{{ list.pricePerUnit }}</p>
        <p>x{{ list.quantity }}</p>
        <p>{{ list.quantity * list.pricePerUnit }}</p>
        <button class="btn" @click="$store.dispatch('removeOrder', list.id)">
          X
        </button>
      </div>
    </div>

    <div class="total">
      <p>Total</p>
      <p>{{ total }}</p>
    </div>

    <div class="button-group">
      <button
        class="btn"
        style="background-color: #5cb85c; color: white"
        @click="checkout"
      >
        Checkout
      </button>
    </div>
  </div>
</template>

<style scoped>
.orders {
  display: grid;
  grid-template-rows: auto 1fr auto 50px;
  gap: 10px;
  margin-left: auto;
  width: 400px !important;
  padding: 10px;
  background-color: rgb(228, 228, 228);
  color: black;
}

.orders > h2 {
  margin: 0;
}

.total {
  display: flex;
  font-weight: bold;
  font-size: 20px;
}

.total > p {
  margin: 0;
}

.total > p:last-child {
  margin-left: auto;
}

.button-group {
  display: flex;
}

.button-group > button {
  flex-grow: 1;
}

.order-list {
  overflow-y: auto;
  overflow-x: hidden;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.list {
  display: grid;
  grid-template-columns: 130px 50px 50px 1fr auto;
  align-items: center;
  gap: 10px;
}

.list > p {
  margin: 0;
}

.list > p:not(:first-child) {
  text-align: right;
}
</style>

<script>
export default {
  props: ["total"],

  methods: {
    checkout() {
      const history = this.$store.state.orderList.map((e) => ({
        id: e.id,
        name: e.name,
        total: e.quantity * e.pricePerUnit,
      }));

      this.$axios.post("http://localhost:3000/history", history);
      this.$store.commit("clearOrderList");
    },
  },
};
</script>