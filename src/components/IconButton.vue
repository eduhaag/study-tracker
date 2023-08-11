<template>
  <button class="button" @click="click" :disabled="disabled">
    <span class="icon">
      <i :class="icon"></i>
    </span>
    <span>{{ text }}</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "IconButton",
  emits: ["click"],
  props: {
    disabled: {
      type: Boolean,
    },
    icon: {
      type: String,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
  },
  methods: {
    click(): void {
      this.$emit("click");
    },
  },
});
</script>
