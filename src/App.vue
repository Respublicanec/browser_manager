<script setup>
import { ref } from "vue";
import CardSeting from "@/components/CardSeting.vue";
import logo from "@/assets/images/logo.svg";
import iconSun from "@/assets/images/icon-sun.svg";

const data = ref([
  {
    logo: "./src/assets/images/logo-devlens.svg",
    name: "DevLens",
    description:
      "Quickly inspect page layouts and visualize element boundaries.",
    isActive: true,
  },
  {
    logo: "./src/assets/images/logo-style-spy.svg",
    name: "StyleSpy",
    description: "Instantly analyze and copy CSS from any webpage element.",
    isActive: true,
  },
  {
    logo: "./src/assets/images/logo-speed-boost.svg",
    name: "SpeedBoost",
    description: "Optimizes browser resource usage to accelerate page loading.",
    isActive: false,
  },
  {
    logo: "./src/assets/images/logo-json-wizard.svg",
    name: "JSONWizard",
    description:
      "Formats, validates, and prettifies JSON responses in-browser.",
    isActive: true,
  },
]);
</script>

<template>
  <div class="header">
    <img class="logo" :src="logo" alt="" />
    <div class="seting-blog">
      <img class="seting-icon" :src="iconSun" alt="" />
    </div>
  </div>
  <div class="filter-container">
    <h2 class="header-filter">Expension list</h2>
    <div class="buttons-filters">
      <button class="button">All</button>
      <button class="button">Active</button>
      <button class="button">Inactive</button>
    </div>
  </div>
  <div class="list-cards">
    <CardSeting v-for="card in data" :card="card" />
  </div>
</template>

<style scoped>
.header {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(2, 3fr);
  background-color: rgb(49, 60, 90);
  border-radius: 20px;
  padding: 10px;
}
.logo {
  padding: 10px;
  color: azure;
}
.seting-blog {
  display: flex;
  align-items: center;
  background-color: rgb(59, 76, 118);
  border-radius: 15px;
  justify-self: end;
}
.seting-icon {
  width: 25px;
  height: 25px;
  margin: 15px;
}
.filter-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  padding: 30px 0;
}
.header-filter {
  color: rgb(247, 247, 247);
  font-size: 50px;
}
.buttons-filters {
  display: flex;
  gap: 10px;
  justify-self: end;
  margin: 20px;
}
.button {
  background-color: rgb(59, 76, 118);
  padding: 10px 20px;
  color: rgb(255, 255, 255);
  font-size: 20px;
  border-radius: 20px;
  border: none;
}
.list-cards {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 15px;
}
</style>
