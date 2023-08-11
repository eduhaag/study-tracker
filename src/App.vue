<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter sidebar">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <SectionForm @finish-section="saveSection" />
      <div class="list">
        <Card v-if="isListEmpty">Você ainda não teve estudos hoje :-(</Card>
        <StudySection
          v-for="(section, index) in studySections"
          :key="index"
          :section="section"
        />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SideBar from "./components/SideBar.vue";
import SectionForm from "./components/SectionForm.vue";
import StudySection from "./components/StudySection.vue";
import IStudySection from "./interfaces/IStudySection";
import Card from "./components/Card.vue";

export default defineComponent({
  name: "App",
  components: {
    SideBar,
    SectionForm,
    StudySection,
    Card,
  },
  data() {
    return {
      studySections: [] as IStudySection[],
    };
  },
  computed: {
    isListEmpty(): boolean {
      return this.studySections.length === 0;
    },
  },
  methods: {
    saveSection(section: IStudySection) {
      this.studySections.push(section);
    },
  },
});
</script>

<style>
.list {
  padding: 1.25rem;
}
</style>
