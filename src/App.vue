<template>
  <div id="app">
    <HeroNav />
    <RouterView />
    <Modal ref="modal" />
    <NewFooter />
    <!-- <button @click="getUser">GET</button> -->
  </div>
</template>

<script setup>
import { ref } from "vue";
import { RouterView } from "vue-router";

import Modal from "./components/Modal.vue";
import NavBar from "./components/NavBar.vue";

import HeroNav from "./components/HeroNav.vue";
import NewFooter from "./components/NewFooter.vue";
import CoolFooter from "./components/CoolFooter.vue";
import TwoNavbar from "./components/TwoNavbar.vue";

import { useLoginStore } from "./stores/login";
import { useCartStore } from "./stores/shoppingCart";

const cartStore = useCartStore();
const store = useLoginStore();

const modal = ref(null);

const openModal = () => {
  modal.value.openModal();
};

async function getUser() {
  const res = await fetch("http://localhost:3001/subscribers");
  const users = await res.json();
  console.log(users);
}
</script>

<style scoped>
.fuu {
  float: left;
  display: block;
  color: black;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

#app {
  display: flex;
  flex-direction: column;
  height: 100vh;
  position: relative;
}

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: "Raleway", sans-serif;
  font-weight: 400;
}

.notification {
  background-color: #555;
  color: white;
  text-decoration: none;
  padding: 15px 26px;
  position: relative;
  display: inline-block;
  border-radius: 2px;
}

.notification:hover {
  background: red;
}

.notification .badge {
  position: absolute;
  top: -10px;
  right: -10px;
  padding: 5px 10px;
  border-radius: 50%;
  background: red;
  color: white;
}
</style>
