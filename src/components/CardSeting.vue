<script setup>
import { ref } from "vue";

const props = defineProps({
  card: {
    type: Object,
  },
});

const emit = defineEmits(["click"]);

const isActive = ref(props.card.isActive);

const toggleActive = () => {
  isActive.value = !isActive.value;
};
</script>

<template>
  <div class="card">
    <div class="header-card">
      <img :src="card.logo" alt="Логотип" />
      <div class="text-header">
        <h2>{{ card.name }}</h2>
        <span class="text">{{ card.description }} </span>
      </div>
    </div>
    <div class="footer-buttons">
      <button class="remove">Remove</button>
      <div class="toggle-container">
        <input type="checkbox" id="toggle" class="toggle-input" />
        <label for="toggle" @click="toggleActive()" class="toggle-label">
          <span
            class="toggle-handle"
            :class="{ 'toggle-activ': isActive }"
          ></span>
        </label>
      </div>
    </div>
  </div>
</template>

<style>
.card {
  display: grid;
  gap: 20px;
  padding: 10px 20px;
  border: 1px solid red;
  background-color: rgb(59, 76, 118);
  max-width: 600px;
  border-radius: 20px;
}
.header-card {
  display: grid;
  grid-template-columns: 1fr 5fr;
  gap: 10px;
  align-items: center;
}
.text-header {
  color: rgb(255, 255, 255);
}
.text {
}
.footer-buttons {
  display: grid;
  grid-template-columns: 1fr 1fr;
  padding: 10px 0;
}
.remove {
  margin-right: auto;
  background-color: rgb(59, 76, 118);
  border: 1px solid white;
  color: rgb(255, 255, 255);
  padding: 10px 20px;
  border-radius: 20px;
}
.toggle-container {
  display: grid;
  margin-left: 100%;
  display: flex;
  position: relative;
  display: inline-block;
  width: 60px;
}

.toggle-input {
  opacity: 0;
}

.toggle-label {
  position: absolute;
  top: 10px;
  right: 50px;
  width: 56px;
  height: 30px;
  background-color: #c7231a;
  display: block;
  border-radius: 15px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.toggle-handle {
  position: absolute;
  top: 5px;
  left: 3px;
  width: 20px;
  height: 20px;
  background-color: white;
  border-radius: 50%;
  transition: transform 0.3s;
}

.toggle-activ {
  transform: translateX(30px);
}
</style>
