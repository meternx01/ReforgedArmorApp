<template>
    <div class="upgrade-item">
      <p>{{ upgradeDetail }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'UpgradeItem',
    props: {
      upgradeDetail: String
    }
  }
  </script>
  
  <style scoped>
  .upgrade-item {
    border: 1px solid #ccc;
    padding: 0.5rem;
    margin: 0.5rem 0;
  }
  </style>