<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <TimerDisplay :time-in-seconds="timeInSeconds" />
    <IconButton
      @click="start"
      :disabled="timerStarted"
      text="Play"
      icon="fas fa-play"
    />
    <IconButton
      @click="stop"
      :disabled="!timerStarted"
      text="Stop"
      icon="fas fa-stop"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TimerDisplay from "./TimerDisplay.vue";
import IconButton from "./IconButton.vue";

export default defineComponent({
  name: "SectionTimer",
  components: {
    TimerDisplay,
    IconButton,
  },
  data() {
    return {
      timeInSeconds: 0,
      cronometer: 0,
      timerStarted: false,
    };
  },
  emits: ["itTimerStoped"],
  methods: {
    start() {
      this.timerStarted = true;
      this.cronometer = setInterval(() => {
        this.timeInSeconds++;
      }, 1000);
    },
    stop() {
      this.timerStarted = false;
      clearInterval(this.cronometer);
      this.$emit("itTimerStoped", this.timeInSeconds);
      this.timeInSeconds = 0;
    },
  },
});
</script>
