<template>
  <div class="header">
    <img class="logo" :src="logo" alt="" />
    <div class="block" @click="colorTheme()">
      <img class="setting-icon" :src="iconSun" alt="" />
    </div>
  </div>

  <div class="filter-container">
    <h2 class="filter">Extension List</h2>
    <div class="buttons-filters">
      <button class="button">All</button>
      <button class="button">Active</button>
      <button class="button">Inactive</button>
    </div>
  </div>
  <div class="list-cards">
    <ExtensionList v-for="card in data" :key="card.id" :card="card" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import ExtensionList from "@/components/ExtensionList.vue";
import logo from "@/assets/images/logo.svg";
import iconSun from "@/assets/images/icon-sun.svg";

const darkTheme = ref(true);

function colorTheme() {
  darkTheme.value = !darkTheme.value;
  console.log(darkTheme.value);
}

const data = ref([
  {
    logo: "../src/assets/images/logo-devlens.svg",
    name: "DevLens",
    description:
      "Quickly inspect page layouts and visualize element boundaries.",
    isActive: true,
  },
  {
    logo: "../src/assets/images/logo-style-spy.svg",
    name: "StyleSpy",
    description: "Instantly analyze and copy CSS from any webpage element.",
    isActive: true,
  },
  {
    logo: "../src/assets/images/logo-speed-boost.svg",
    name: "SpeedBoost",
    description: "Optimizes browser resource usage to accelerate page loading.",
    isActive: false,
  },
  {
    logo: "../src/assets/images/logo-json-wizard.svg",
    name: "JSONWizard",
    description:
      "Formats, validates, and prettifies JSON responses in-browser.",
    isActive: true,
  },
  {
    logo: "../src/assets/images/logo-tab-master-pro.svg",
    name: "TabMaster Pro",
    description: "Organizes browser tabs into groups and sessions.",
    isActive: true,
  },
  {
    logo: "../src/assets/images/logo-viewport-buddy.svg",
    name: "ViewportBuddy",
    description:
      "Simulates various screen resolutions directly within the browser.",
    isActive: false,
  },
  {
    logo: "../src/assets/images/logo-markup-notes.svg",
    name: "Markup Notes",
    description:
      "Enables annotation and notes directly onto webpages for collaborative debugging.",
    isActive: true,
  },
  {
    logo: "../src/assets/images/logo-grid-guides.svg",
    name: "GridGuides",
    description:
      "Overlay customizable grids and alignment guides on any webpage.",
    isActive: false,
  },
  {
    logo: "../src/assets/images/logo-palette-picker.svg",
    name: "Palette Picker",
    description: "Instantly extracts color palettes from any webpage.",
    isActive: true,
  },
  {
    logo: "../src/assets/images/logo-link-checker.svg",
    name: "LinkChecker",
    description: "Scans and highlights broken links on any page.",
    isActive: true,
  },
  {
    logo: "../src/assets/images/logo-dom-snapshot.svg",
    name: "DOM Snapshot",
    description: "Capture and export DOM structures quickly.",
    isActive: false,
  },
  {
    logo: "../src/assets/images/logo-console-plus.svg",
    name: "ConsolePlus",
    description:
      "Enhanced developer console with advanced filtering and logging.",
    isActive: true,
  },
]);
</script>

<style scoped>
.header {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(2, 3fr);
  background-color: #1f2535;
  border-radius: 20px;
  padding: 7px;
}
.logo {
  padding: 10px;
  color: azure;
}
.block {
  display: flex;
  align-items: center;
  background-color: #2f354b;
  border-radius: 10px;
  justify-self: end;
  margin-right: 12px;
}
.setting-icon {
  width: 22px;
  height: 22px;
  margin: 12px;
}
.filter-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  color: rgb(247, 247, 247);
  padding: 50px 0 10px 0;
}
.filter {
  color: rgb(247, 247, 247);
  font-size: 40px;
}
.buttons-filters {
  display: flex;
  gap: 10px;
  justify-self: end;
  margin: 20px;
}
.button {
  background-color: #2f354b;
  padding: 10px 20px;
  color: rgb(255, 255, 255);
  font-size: 20px;
  border-radius: 20px;
  border: none;
}
.list-cards {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 12px;
}
</style>
