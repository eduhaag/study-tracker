<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de um novo estudo"
      >
        <input
          type="text"
          class="input"
          placeholder="O que você irá estudar agora?"
          v-model="description"
        />
      </div>
      <div class="column">
        <SectionTimer @it-timer-stoped="handleTimerStopped" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SectionTimer from "./SectionTimer.vue";

export default defineComponent({
  name: "SectionForm",
  data() {
    return {
      description: "",
    };
  },
  components: {
    SectionTimer,
  },
  emits: ["finishSection"],
  methods: {
    handleTimerStopped(sectionTime: number): void {
      this.$emit("finishSection", {
        durationInSconds: sectionTime,
        description: this.description,
      });
      this.description = "";
    },
  },
});
</script>

<style scoped></style>
