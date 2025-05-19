<template>
  <button class="button" :class="{ 'button-white': !props.darkTheme }">
    {{ title }}
  </button>
</template>
<script setup>
const props = defineProps({
  title: {
    type: String,
  },
  darkTheme: {
    type: Boolean,
  },
});
</script>
<style scoped>
.button {
  background-color: #2f354b;
  padding: 10px 20px;
  font-family: "NotoSans", sans-serif;
  color: rgb(255, 255, 255);
  font-size: 20px;
  border-radius: 50px;
  border: none;
}

.button-white {
  background-color: #fcfdff;
  color: #000000;
}
</style>
