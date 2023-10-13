<template>
  <div class="item-page">
    <RouterLink to="/">
      <img :src="`../${data.data[product].image}`" />
    </RouterLink>
    <p>{{ data.data[product].description }}</p>
  </div>
</template>

<script setup>
const props = defineProps(["product"]);
import { useDataStore } from "../stores/data";
const data = useDataStore();
</script>

<style scoped>
.item-page {
  display: flex;
  flex-direction: column;

  margin: auto 0;
}

img {
  height: 500px;

  @media (max-width: 750px) {
    height: 200px;
    width: 100%;
  }
}
</style>
