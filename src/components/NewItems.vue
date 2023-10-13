<template>
  <div class="grid-container">
    <div class="box">
      <div class="items cards" v-for="(item, index) in store.data" :key="index">
        <RouterLink :to="`/items/${index}`" class="item-thumb">
          <img :src="item.image" />
        </RouterLink>
        <div class="card-bottom">
          <div>{{ item.name }}</div>
          <div>{{ "$" + item.cost }}</div>
          <div>{{ store.newItem }}</div>
          <button @click="addItem(index)">ADD TO CART</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { useDataStore } from "../stores/data";
import { useCartStore } from "../stores/shoppingCart";

const store = useDataStore();
const { addItem } = useCartStore();
</script>

<style scoped>
/* .grid-container {
  display: flex;
  flex-wrap: wrap;
  transition: 0.5s;
} */

.box {
  display: flex;
  flex-wrap: wrap;
  min-height: 100vh;
  width: 100%;
  max-width: 1200px;
  padding: 15px;
}

.items img:hover {
  transform: scale(1.05);
  position: relative;
  z-index: 0;
}

.grid-container {
  display: flex;
  width: 100%;
  justify-content: center;
  align-items: center;
  padding: 10px;
  flex: 1 0 auto;
}

img {
  height: 100px;
  width: 100px;
  transition: 0.3s;
}

.items {
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
  width: calc(100% / 3 - 10px);
  margin: 5px 5px 0 5px;

  @media (max-width: 750px) {
    width: 100%;
  }
}

.item-thumb {
  width: 100%;
  text-align: center;
}

.cards {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);

  background-color: aliceblue;

  .card-bottom {
    width: 100%;
    border-top: 1px solid gray;
    text-align: center;
  }
}

/* .items {
  display: block;
} */

/* .item-container {
  display: inline-block;
  text-align: center;
} */
/* .responsive {
  display: block;
  padding: 0 6px;
  float: left;
  width: 24.99999%;
} */

#myBtn {
  display: none;
  position: fixed;
  bottom: 20px;
  right: 30px;
  z-index: 99;
  border: none;
  outline: none;
  background-color: red;
  color: white;
  cursor: pointer;
  padding: 15px;
  border-radius: 10px;
  font-size: 18px;
}
</style>
