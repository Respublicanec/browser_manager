<template>
  <div class="card" :class="{ white: !props.darkTheme }">
    <div class="header">
      <img class="card-logo" :src="card.logo" alt="Логотип" />
      <div class="text-header">
        <h2 class="name" :class="{ white: !props.darkTheme }">
          {{ card.name }}
        </h2>
        <span class="text">{{ card.description }} </span>
      </div>
    </div>

    <div class="buttons">
      <button class="remove" :class="{ white: !props.darkTheme }">
        Remove
      </button>
      <div class="toggle-container">
        <input type="checkbox" id="toggle" class="input" />
        <label
          for="toggle"
          @click="switching()"
          class="label"
          :class="{
            'label-red': isActive && props.darkTheme,
            'label-dark-red': isActive && !props.darkTheme,
            'label-white': !isActive && !props.darkTheme,
          }"
        >
          <span class="handle" :class="{ active: isActive }"></span>
        </label>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps({
  card: {
    type: Object,
  },
  darkTheme: {
    type: Boolean,
  },
});

const emit = defineEmits(["click"]);

const isActive = ref(props.card.isActive);

const switching = () => {
  isActive.value = !isActive.value;
};
</script>

<style>
.card {
  display: grid;
  gap: 52px;
  padding: 12px 10px 12px 20px;
  border: 1px solid #393e51;
  background-color: #1f2535;
  max-width: 600px;
  border-radius: 20px;
}
.header {
  display: grid;
  grid-template-columns: 1fr 5fr;
  gap: 15px;
  align-items: center;
}
.text-header {
  align-self: start;
  position: relative;
  color: rgb(255, 255, 255);
}
.name {
  font-size: 21px;
}
.text {
  font-size: 15px;
  position: absolute;
  color: #a9adb8;
}
.card-logo {
  align-self: start;
  padding-top: 5px;
}
.buttons {
  display: grid;
  grid-template-columns: 1fr 1fr;
  height: 57px;
  padding: 10px 0;
  margin-top: auto;
}
.remove {
  margin-right: auto;
  background-color: #1f2533;
  border: 1px solid #d9dadc;
  color: #cbd0d6;
  padding: 10px 15px;
  border-radius: 20px;
  font-size: 16px;
}
.white {
  background-color: #fcfdff;
  color: #16214f;
}
.toggle-container {
  display: grid;
  margin-left: 100%;
  display: flex;
  position: relative;
  display: inline-block;
  width: 60px;
}

.input {
  opacity: 0;
}

.label {
  position: absolute;
  top: 10px;
  right: 70px;
  width: 35px;
  height: 20px;
  background-color: #545a6a;
  display: block;
  border-radius: 15px;
  cursor: pointer;
  transition: background-color 0.3s;
}
.label-red {
  background-color: #f15c55;
}
.label-dark-red {
  background-color: #cf201d;
}
.label-white {
  background-color: #c6c6c6;
}

.handle {
  position: absolute;
  top: 2px;
  left: 2px;
  width: 16px;
  height: 16px;
  background-color: white;
  border-radius: 50%;
  transition: transform 0.3s;
}

.active {
  transform: translateX(15px);
}
</style>
