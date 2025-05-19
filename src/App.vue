<template>
  <div class="header" :class="{ white: !darkTheme }">
    <img class="logo" :src="darkTheme ? logoLight : logoDark" alt="" />
    <div class="block" :class="{ 'block-white': !darkTheme }" tabindex="0">
      <img
        class="setting-icon"
        :class="{ 'setting-white': !darkTheme }"
        :src="darkTheme ? iconSun : iconMoon"
        alt=""
        @click="colorTheme()"
      />
    </div>
  </div>

  <div class="container">
    <h2 class="filter" :class="{ 'filter-white': !darkTheme }">
      Extensions List
    </h2>
    <div class="buttons">
      <FilterButton title="All" :darkTheme="darkTheme" />
      <FilterButton title="Active" :darkTheme="darkTheme" />
      <FilterButton title="Inactive" :darkTheme="darkTheme" />
    </div>
  </div>

  <div class="list-cards">
    <Extension
      v-for="card in data"
      :key="card.name"
      :card="card"
      :darkTheme="darkTheme"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";
import Extension from "@/components/Extension.vue";
import FilterButton from "@/components/FilterButton.vue";
import logoLight from "/images/logo.svg";
import logoDark from "/images/logo2.svg";
import iconSun from "/images/icon-sun.svg";
import iconMoon from "/images/icon-moon.svg";

const darkTheme = ref(true);

const colorTheme = () => {
  darkTheme.value = !darkTheme.value;
  if (darkTheme.value) {
    document.body.classList.remove("body-white");
  } else {
    document.body.classList.add("body-white");
  }
};

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
  background-color: #1f2535;
  border: 3px solid transparent;
  border-radius: 15px;
  justify-self: end;
  padding: 3px;
  margin-right: 5px;
}

.block:focus {
  border: 3px solid red;
}

.block-white {
  background-color: #fcfdff;
}

.setting-icon {
  background-color: #2f354b;
  width: 50px;
  height: 50px;
  padding: 14px;
  margin: 1px;
  border-radius: 10px;
}

.setting-icon:hover {
  background-color: #515868;
}

.setting-white {
  background-color: #f6f5f5;
}

.setting-white:hover {
  background-color: #c2c3c3;
}

.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  color: rgb(247, 247, 247);
  padding: 58px 0 22px 0;

  @media (max-width: 650px) {
    text-align: center;
    grid-template-columns: 1fr;
    padding: 30px 0 8px 0;
  }
}

.filter {
  font-family: "NotoSans", sans-serif;
  font-weight: bold;
  color: rgb(247, 247, 247);
  font-size: 34px;
}

.filter-white {
  color: #0b1645;
}

.container .buttons {
  display: flex;
  padding-top: 6px;
  gap: 10px;
  justify-self: end;
  @media (max-width: 650px) {
    justify-self: center;
  }
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
