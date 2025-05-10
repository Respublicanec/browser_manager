<script setup>
import icon1 from "@/assets/images/logo-markup-notes.svg";
</script>

<template>
  <div class="header_card">
    <img :src="icon1" alt="Логотип" />
    <div>
      <h2>DevLens</h2>
      <span>Quickly Quickly QuicklyQuickly </span>
    </div>
  </div>
  <div>
    <button>Remove</button>
    <button></button>
  </div>
</template>

<style>
.header_card {
  display: grid;
  grid-template-columns: repeat(2, 3fr);
}
</style>
