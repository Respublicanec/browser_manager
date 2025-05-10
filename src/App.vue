<script setup>
import CardSeting from "@/components/CardSeting.vue";
import logo from "@/assets/images/logo.svg";
import iconSun from "@/assets/images/icon-sun.svg";
</script>

<template>
  <div class="header">
    <img class="logo" :src="logo" alt="" />
    <div class="seting_blog">
      <img class="seting_icon" :src="iconSun" alt="" />
    </div>
  </div>
  <div class="filter_container">
    <h2 class="header_filter">Expension list</h2>
    <div class="buttons_filters">
      <button class="button">All</button>
      <button class="button">Active</button>
      <button class="button">Inactive</button>
    </div>
  </div>
  <div>
    <CardSeting />
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
.seting_blog {
  display: flex;
  align-items: center;
  background-color: rgb(59, 76, 118);
  border-radius: 15px;
  justify-self: end;
}
.seting_icon {
  width: 25px;
  height: 25px;
  margin: 15px;
}
.filter_container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  padding: 30px 0;
}
.header_filter {
  color: rgb(247, 247, 247);
  font-size: 50px;
}
.buttons_filters {
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
</style>
