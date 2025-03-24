<template>
  <div class="armor-card">
    <!-- Left side: current armor details -->
    <div class="current-armor">
      <img :src="currentArmor.LinkURL" alt="Armor Icon" class="armor-icon" />
      <h3 class="armor-name">{{ currentArmor.Name }}</h3>
    </div>

    <!-- Right side: upgrade paths in a 2-column grid -->
    <div class="upgrade-paths">
      <div class="upgrade-card" v-for="upgrade in currentArmor.upgradePaths" :key="upgrade.name">
        <div class="upgrade-header">
          <img :src="upgrade.LinkURL" alt="Upgrade Icon" class="upgrade-icon" />
          <!-- Larger upgrade name -->
          <span class="upgrade-name">{{ upgrade.name }}</span>
        </div>
        <ul class="requirements">
          <li v-for="req in upgrade.requirements" :key="req.item">
            <!-- Bold requirement item name -->
            <span class="req-name">{{ req.item }}</span>: {{ req.quantity }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ArmorCard',
  props: {
    currentArmor: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.armor-card {
  display: flex;
  border: 1px solid #ccc;
  padding: 1rem;
  margin: 1rem 0;
  border-radius: 10px;
  overflow: hidden;
}

/* Left side: Armor name + icon */
.current-armor {
  width: 20%;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  padding-right: 1rem;
  border-right: 1px solid #ccc;
}

.armor-icon {
  width: 80px;
  height: 80px;
  object-fit: contain;
  margin-right: 0.5rem;
}

.armor-name {
  font-size: 1.2rem;
  text-align: center;
}

/* Right side: 2-column grid for upgrade paths */
.upgrade-paths {
  flex: 1;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
  padding-left: 1rem;
}

.upgrade-card {
  border: 1px solid #ddd;
  padding: 0.5rem;
  border-radius: 10px;
  text-align: center;
}

.upgrade-header {
  display: flex;
  align-items: center;
  margin-bottom: 0.5rem;
}

.upgrade-icon {
  width: 50px;
  height: 50px;
  object-fit: contain;
  margin-right: 0.5rem;
}

.upgrade-name {
  font-size: 1.25rem; /* Make the upgrade name bigger */
  margin: 0;
  line-height: 50px; /* Vertically center text with the icon's height */
}

/* Bold the requirement item name */
.req-name {
  font-weight: bold;
}

/* Requirements list */
.requirements {
  list-style-type: none;
  padding: 0;
  margin-top: 0.5rem;
  font-size: 0.8rem;
  text-align: left;
}

/* Mobile adjustments */
@media (max-width: 768px) {
  .armor-card {
    flex-direction: column;
  }

  .current-armor {
    width: 100%;
    border-right: none;
    border-bottom: 1px solid #ccc;
    padding-right: 0;
    padding-bottom: 1rem;
    margin-bottom: 1rem;
  }

  .upgrade-paths {
    grid-template-columns: 1fr; /* single column on small screens */
    padding-left: 0;
  }
}
</style>