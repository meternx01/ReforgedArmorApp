<template>
    <div class="armor-picker">
      <h2>Select Armor Set</h2>
      <div class="set-selector">
        <button @click="selectSet('Artifact')" :class="{ active: selectedSet === 'Artifact' }">Artifact</button>
        <button @click="selectSet('Relic')" :class="{ active: selectedSet === 'Relic' }">Relic</button>
        <button @click="selectSet('Empyrean')" :class="{ active: selectedSet === 'Empyrean' }">Empyrean</button>
      </div>
      <div class="armor-display">
        <ArmorCard v-for="armor in currentArmors" :key="armor.Name" :currentArmor="armor" />
      </div>
    </div>
  </template>
  
  <script>
  import ArmorCard from './ArmorCard.vue'
  import artifactData from '../assets/Artifact.json'
  import relicData from '../assets/Relic.json'
  import empyreanData from '../assets/Empyrean.json'
  
  export default {
    name: 'ArmorPicker',
    components: {
      ArmorCard
    },
    props: {
      job: {
        type: String,
        default: null
      }
    },
    data() {
      return {
        selectedSet: 'Artifact', // default selection
        sets: {
          Artifact: artifactData,
          Relic: relicData,
          Empyrean: empyreanData
        }
      }
    },
    computed: {
      currentArmors() {
        // Get all armors from the selected set
        const armors = this.sets[this.selectedSet] || []
        // If a job is selected, filter the armors by that job
        return this.job ? armors.filter(item => item.Job === this.job) : armors
      }
    },
    methods: {
      selectSet(set) {
        this.selectedSet = set
      }
    }
  }
  </script>
  

  <style scoped>
  .armor-picker {
    padding: 1rem;
  }
  
  .set-selector {
    margin-bottom: 1rem;
  }
  
  .set-selector button {
    margin-right: 0.5rem;
    padding: 0.5rem 1rem;
    /* border: 1px solid #ccc; */
    /* background: #fff; */
    border-radius: 5px;
    cursor: pointer;
  }
  
  .set-selector button.active {
    background: #ddd;
  }
  
  .armor-display {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
  </style>