<template>
  <div class="card" :class="whiteTeme">
    <div class="header">
      <img class="logo" :src="card.logo" alt="Логотип" />
      <div class="text-header">
        <h2 class="name" :class="whiteTeme">
          {{ card.name }}
        </h2>
        <span class="text">{{ card.description }} </span>
      </div>
    </div>

    <div class="buttons">
      <button class="remove" :class="whiteTeme">Remove</button>
      <div class="toggle-container">
        <input
          type="checkbox"
          :id="card.name"
          v-model="isActive"
          class="input"
        />
        <div class="substrate" tabindex="0">
          <div
            :for="card.name"
            @click="isActive.value = !isActive.value"
            class="label"
            :class="colorTheme"
          >
            <span class="handle" :class="{ active: isActive }"></span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

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

const whiteTeme = computed(() => ({
  white: !props.darkTheme,
}));

const colorTheme = computed(() => ({
  "label-red": isActive.value && props.darkTheme,
  "label-dark-red": isActive.value && !props.darkTheme,
  "label-white": !isActive.value && !props.darkTheme,
}));
</script>

<style>
.card {
  display: grid;
  gap: 52px;
  padding: 13px 10px 8px 20px;
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

.card .logo {
  align-self: start;
  padding-top: 5px;
}

.buttons {
  display: grid;
  grid-template-columns: 1fr 1fr;
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

.buttons .toggle-container {
  display: grid;
  margin-left: 100%;
  display: flex;
  position: relative;
  display: inline-block;
  width: 60px;
}

.input {
  position: absolute;
  right: 73px;
  top: 8px;
  width: 38px;
  height: 35px;
  z-index: 1;
  /* display: none; */
  opacity: 0;
}

.label {
  position: relative;
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

.substrate {
  position: absolute;
  display: grid;
  justify-items: center;
  align-items: center;
  top: 10px;
  border: 2px solid transparent;
  border-radius: 15px;
  right: 70px;
  width: 43px;
  height: 28px;
}

.substrate:focus {
  border: 2px solid red;
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
