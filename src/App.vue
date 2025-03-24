<template>
  <div id="app">
    <Header />
    <main>
      <JobSelector @job-selected="handleJobSelect" />
      <div v-if="selectedJob">
        <h2>Armor Upgrades for {{ selectedJob }}</h2>
        <!-- Pass the selected job to ArmorPicker -->
        <ArmorPicker :job="selectedJob" />
      </div>
    </main>
  </div>
</template>


<script>
import Header from './components/Header.vue'
import JobSelector from './components/JobSelector.vue'
import ArmorPicker from './components/ArmorPicker.vue'

export default {
  name: 'App',
  components: {
    Header,
    JobSelector,
    ArmorPicker
  },
  data() {
    return {
      selectedJob: null
    }
  },
  methods: {
    handleJobSelect(job) {
      this.selectedJob = job;
    }
  }
}
</script>





<style>
/* Global styles */
</style>