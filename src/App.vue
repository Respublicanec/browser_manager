<template>
  <div class="header" :class="{ white: !darkTheme }">
    <img class="logo" :src="darkTheme ? logo : logo2" alt="" />
    <div
      class="block"
      :class="{ blockWhite: !darkTheme }"
      @click="colorTheme()"
    >
      <img class="setting-icon" :src="darkTheme ? iconSun : iconMoon" alt="" />
    </div>
  </div>

  <div class="container">
    <h2 class="filter" :class="{ 'filter-white': !darkTheme }">
      Extensions List
    </h2>
    <div class="buttons">
      <button class="button">All</button>
      <button class="button">Active</button>
      <button class="button">Inactive</button>
    </div>
  </div>

  <div class="list-cards">
    <Extension
      v-for="card in data"
      :key="card.id"
      :card="card"
      :darkTheme="darkTheme"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";
import Extension from "@/components/Extension.vue";
import logo from "/images/logo.svg";
import logo2 from "/images/logo2.svg";
import iconSun from "/images/icon-sun.svg";
import iconMoon from "/images/icon-moon.svg";

const darkTheme = ref(true);

function colorTheme() {
  darkTheme.value = !darkTheme.value;
  if (darkTheme.value) {
    document.body.classList.remove("body-White");
  } else {
    document.body.classList.add("body-White");
  }
}

const data = ref([
  {
    logo: "/images/logo-devlens.svg",
    name: "DevLens",
    description:
      "Quickly inspect page layouts and visualize element boundaries.",
    isActive: true,
  },
  {
    logo: "/images/logo-style-spy.svg",
    name: "StyleSpy",
    description: "Instantly analyze and copy CSS from any webpage element.",
    isActive: true,
  },
  {
    logo: "/images/logo-speed-boost.svg",
    name: "SpeedBoost",
    description: "Optimizes browser resource usage to accelerate page loading.",
    isActive: false,
  },
  {
    logo: "/images/logo-json-wizard.svg",
    name: "JSONWizard",
    description:
      "Formats, validates, and prettifies JSON responses in-browser.",
    isActive: true,
  },
  {
    logo: "/images/logo-tab-master-pro.svg",
    name: "TabMaster Pro",
    description: "Organizes browser tabs into groups and sessions.",
    isActive: true,
  },
  {
    logo: "/images/logo-viewport-buddy.svg",
    name: "ViewportBuddy",
    description:
      "Simulates various screen resolutions directly within the browser.",
    isActive: false,
  },
  {
    logo: "/images/logo-markup-notes.svg",
    name: "Markup Notes",
    description:
      "Enables annotation and notes directly onto webpages for collaborative debugging.",
    isActive: true,
  },
  {
    logo: "/images/logo-grid-guides.svg",
    name: "GridGuides",
    description:
      "Overlay customizable grids and alignment guides on any webpage.",
    isActive: false,
  },
  {
    logo: "/images/logo-palette-picker.svg",
    name: "Palette Picker",
    description: "Instantly extracts color palettes from any webpage.",
    isActive: true,
  },
  {
    logo: "/images/logo-link-checker.svg",
    name: "LinkChecker",
    description: "Scans and highlights broken links on any page.",
    isActive: true,
  },
  {
    logo: "/images/logo-dom-snapshot.svg",
    name: "DOM Snapshot",
    description: "Capture and export DOM structures quickly.",
    isActive: false,
  },
  {
    logo: "/images/logo-console-plus.svg",
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

  @media (max-width: 650px) {
    padding: 3px;
  }
}
.white {
  background-color: #fcfdff;
  border: 1px solid #dde5f0;
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
.blockWhite {
  background-color: #eeeeee;
}
.setting-icon {
  width: 22px;
  height: 22px;
  margin: 12px;
}
.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  color: rgb(247, 247, 247);
  padding: 58px 0 2px 0;

  @media (max-width: 650px) {
    text-align: center;
    grid-template-columns: 1fr;
    padding: 30px 0 8px 0;
  }
}
.filter {
  font-family: "NotoSans", sans-serif; /* Обычный шрифт */
  font-weight: bold;
  color: rgb(247, 247, 247);
  font-size: 34px;
}
.filter-white {
  color: #0b1645;
}
.buttons {
  display: flex;
  gap: 10px;
  justify-self: end;
  margin: 20px;
  @media (max-width: 650px) {
    justify-self: center;
  }
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

  @media (max-width: 1024px) {
    grid-template-columns: 1fr 1fr;
  }

  @media (max-width: 650px) {
    grid-template-columns: 1fr;
  }
}
</style>
