<template>
    <div>
      <h2 v-if="job">Armor Upgrades for {{ job }}</h2>
      <div v-if="filteredArtifacts.length">
        <ArmorCard
          v-for="artifact in filteredArtifacts"
          :key="artifact.Name"
          :currentArmor="artifact"
        />
      </div>
      <div v-else>
        <p>No upgrades available for the selected job.</p>
      </div>
    </div>
  </template>



  <script>
  import artifactData from '../assets/Artifact.json'
  import ArmorCard from './ArmorCard.vue'

  export default {
    name: 'ArmorUpgrade',
    props: {
      job: {
        type: String,
        default: null
      }
    },
    components: {
      ArmorCard
    },
    computed: {
      filteredArtifacts() {
        if (!this.job) return [];
        return artifactData.filter(item => item.Job === this.job);
      }
    }
  }
  </script>


  <style scoped>
  .artifact {
    border: 1px solid #ccc;
    margin: 1rem 0;
    padding: 1rem;
  }
  .artifact h3 {
    margin-bottom: 0.5rem;
  }
  .artifact ul {
    list-style: none;
    padding-left: 0;
  }
  .artifact li {
    margin-bottom: 0.25rem;
  }
  .armor-card {
  display: flex;
  flex-direction: row;
  border: 4px solid #ccc;
  padding: 1rem;
  margin: 1rem 0;
  border-radius: 10px; /* This creates rounded corners */
  overflow: hidden; /* Optional: helps clip children that might overflow the rounded corners */
}
  </style>
