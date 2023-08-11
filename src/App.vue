<template>
  <main
    class="columns is-gapless is-multiline"
    :class="{ 'dark-mode': isDarkModeActive }"
  >
    <div class="column is-one-quarter sidebar">
      <SideBar @theme-changed="changeMode" />
    </div>
    <div class="column is-three-quarter content">
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
      isDarkModeActive: false,
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

    changeMode(isDarkModeActive: boolean) {
      this.isDarkModeActive = isDarkModeActive;
    },
  },
});
</script>

<style>
.list {
  padding: 1.25rem;
}

main {
  --bg-primary: #fff;
  --bg-secundary: #ccf3b6;
  --text-primary: #666;
}

main.dark-mode {
  --bg-primary: #35495e;
  --bg-secundary: #41b883;
  --text-primary: #eee;
}

.content {
  background-color: var(--bg-primary);
}
</style>
