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
  position: relative;
  z-index: 1;
  background-color: #2f354b;
  padding: 10px 20px;
  font-family: "NotoSans", sans-serif;
  color: #ffffff;
  font-size: 20px;
  border-radius: 50px;
  border: none;
  cursor: pointer;
}

.button:focus:before {
  content: "";
  position: absolute;
  border: 2px solid #bf1616;
  border-radius: 32px;
  top: -4px;
  left: -4px;
  right: -4px;
  bottom: -4px;
}

.button:hover {
  background-color: #525868;
  color: #ffffff;
}

.button-white {
  background-color: #fcfdff;
  color: #000000;
}
.button-white:hover {
  background-color: #fcfdff;
  color: #828080;
}
</style>
