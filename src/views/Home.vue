<template>
  <div class="layout">
    <div class="main">
      <div class="products"></div>

      <div class="orders">
        <h2>Orders</h2>

        <div class="order-list">
          <div class="list" v-for="i in 100" :key="i">asdf {{ i }}</div>
        </div>

        <div class="total">
          <p>Total</p>
          <p>{{ total }}</p>
        </div>

        <div class="button-group">
          <button class="btn" style="background-color: #5cb85c; color: white">
            Checkout
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.main {
  display: flex;
  flex-grow: 1;
  max-height: 100vh;
}

.orders {
  display: grid;
  grid-template-rows: 50px 1fr 50px 50px;
  gap: 10px;
  /* align-items: center; */
  margin-left: auto;
  min-width: 300px;
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
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>

<script>
export default {
  name: "Home",
  data() {
    return {
      total: 0,
      orderList: [
        {
          name: "Lollipop",
          quantity: 1,
          pricePerUnit: 20,
        },
        {
          name: "Snake",
          quantity: 1,
          pricePerUnit: 50,
        },
        {
          name: "Cat",
          quantity: 1,
          pricePerUnit: 200,
        },
        {
          name: "Dog",
          quantity: 1,
          pricePerUnit: 250,
        },
        {
          name: "Computer",
          quantity: 1,
          pricePerUnit: 50000,
        },
        {
          name: "Mouse",
          quantity: 1,
          pricePerUnit: 1379,
        },
      ],
    };
  },
};
</script>
