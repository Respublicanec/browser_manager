<template>
  <div class="card">
    <div class="header">
      <img class="card-logo" :src="card.logo" alt="Логотип" />
      <div class="text-header">
        <h2>{{ card.name }}</h2>
        <span class="text">{{ card.description }} </span>
      </div>
    </div>
    <div class="footer-buttons">
      <button class="remove">Remove</button>
      <div class="toggle-container">
        <input type="checkbox" id="toggle" class="toggle-input" />
        <label
          for="toggle"
          @click="switching()"
          class="toggle-label"
          :class="{ 'label-red': isActive }"
        >
          <span
            class="toggle-handle"
            :class="{ 'toggle-activ': isActive }"
          ></span>
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
  padding: 12px 20px;
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
.text {
  position: absolute;
}
.card-logo {
  align-self: start;
  padding-top: 5px;
}
.footer-buttons {
  display: grid;
  grid-template-columns: 1fr 1fr;
  height: 57px;
  padding: 10px 0;
  margin-top: auto;
}
.remove {
  margin-right: auto;
  background-color: #1f2533;
  border: 1px solid white;
  color: rgb(255, 255, 255);
  padding: 10px 15px;
  border-radius: 20px;
  font-size: 16px;
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
  right: 60px;
  width: 35px;
  height: 20px;
  background-color: #525867;
  display: block;
  border-radius: 15px;
  cursor: pointer;
  transition: background-color 0.3s;
}
.label-red {
  background-color: #f15c55;
}

.toggle-handle {
  position: absolute;
  top: 2px;
  left: 2px;
  width: 16px;
  height: 16px;
  background-color: white;
  border-radius: 50%;
  transition: transform 0.3s;
}

.toggle-activ {
  transform: translateX(15px);
}
</style>
