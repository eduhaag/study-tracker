<template>
  <header
    class="is-flex is-flex-direction-column is-align-items-center is-justify-content-center"
  >
    <img src="../assets/logo.png" alt="" />
    <h1>Vue - Study Timer</h1>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "SideBar",
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
  position: fixed;
  top: 50%;
}

img {
  max-width: 5rem;
  position: fixed;
  top: 35%;
}

@media only screen and(max-width: 768px ) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
