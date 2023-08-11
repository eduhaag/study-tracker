<template>
  <div class="box has-text-weight-bold study-section">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "CardBox",
});
</script>

<style>
.study-section {
  background: var(--bg-secundary);
  color: var(--text-primary);
}
</style>
