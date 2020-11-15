<template>
  <div class="product-card" @click="$emit('click')">
    <p>{{ name }}</p>
    <p>{{ price }}</p>
  </div>
</template>

<style scoped>
.product-card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  width: 100px;
  height: 100px;
  background-color: lightblue;
  box-shadow: 0 0 3px gray;
}

.product-card > p {
  margin: 0;
}
</style>

<script>
export default {
  props: ["name", "price"],
};
</script>