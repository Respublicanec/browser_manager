<template>
  <button class="button" :class="colorThesme">
    {{ title }}
  </button>
</template>
<script setup>
import { ref, computed } from "vue";

const props = defineProps({
  title: {
    type: String,
  },
  darkTheme: {
    type: Boolean,
  },
  active: {
    type: Boolean,
  },
});

const colorThesme = computed(() => ({
  "button-white": !props.darkTheme && !props.active,
  "button-red": props.darkTheme && props.active,
  "button-white-red": !props.darkTheme && props.active,
}));
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

.button-red {
  background-color: #f35c55;
  color: #000000;
}

.button-red:hover {
  background-color: #dc4941;
  color: #000000;
}

.button-white-red {
  background-color: #dc4941;
  color: #fcfdff;
}

.button-white-red:hover {
  background-color: #f35c55;
  color: #fcfdff;
}
</style>
