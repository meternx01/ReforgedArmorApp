<template>
    <div>
      <h2>Select a Job</h2>
      <div v-if="jobs.length">
        <button v-for="job in jobs" :key="job" @click="selectJob(job)">
          {{ job }}
        </button>
      </div>
      <div v-else>
        Loading jobs...
      </div>
    </div>
  </template>
  
  <script>
import artifactData from '../assets/Artifact.json'

export default {
  name: 'JobSelector',
  data() {
    return {
      jobs: []
    }
  },
  created() {
    // Extract unique job names from the imported JSON
    const uniqueJobs = Array.from(new Set(artifactData.map(item => item.Job)));
    this.jobs = uniqueJobs;
  },
  methods: {
    selectJob(job) {
      this.$emit('job-selected', job);
    }
  }
}
</script>

  

  <style scoped>
  button {
    margin: 0.5rem;
    padding: 0.5rem 1rem;
  }
  </style>
