<template>
  <Card>
    <div class="columns">
      <div class="column is-7">
        {{ section.description || "Sem descrição" }}
      </div>
      <div class="column">
        <TimerDisplay :time-in-seconds="section.durationInSconds" />
      </div>
    </div>
  </Card>
</template>

<script lang="ts">
import { PropType, defineComponent } from "vue";
import TimerDisplay from "./TimerDisplay.vue";
import IStudySection from "@/interfaces/IStudySection";
import Card from "./Card.vue";

export default defineComponent({
  name: "StudySection",
  components: { TimerDisplay, Card },
  props: {
    section: {
      type: Object as PropType<IStudySection>,
      required: true,
    },
  },
});
</script>
