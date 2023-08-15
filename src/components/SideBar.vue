<template>
  <header class="is-flex is-justify-content-center">
    <div
      class="is-flex is-flex-direction-column is-align-items-center is-justify-content-center logo"
    >
      <img src="../assets/logo.png" alt="" />
      <h1>Vue - Study Tracker</h1>
      <Toggle @toogle-changed="handleChangeTheme" />
    </div>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Toggle from "./Toggle.vue";

export default defineComponent({
  name: "SideBar",
  components: {
    Toggle,
  },
  emits: ["themeChanged"],

  methods: {
    handleChangeTheme(isDarkModeActive: boolean) {
      this.$emit("themeChanged", isDarkModeActive);
    },
  },
});
</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100%;
  min-height: 100vh;
}

h1 {
  color: #fff;
  font-size: 1.5rem;
  text-align: center;
}

img {
  max-width: 5rem;
}

.logo {
  position: fixed;
  top: 2rem;
  gap: 1rem;
}

@media only screen and(max-width: 768px ) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
