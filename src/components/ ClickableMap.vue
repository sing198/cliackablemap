<!-- src/components/ClickableMap.vue -->
<template>
  <div class="map-container">
    <svg viewBox="0 0 1000 500" @click="handleMapClick($event)">
      <!-- Example clickable regions; replace with actual SVG path data for a real map -->
      <path
        v-for="(region, index) in regions"
        :key="index"
        :d="region.d"
        :fill="region.color"
        @click.stop="handleRegionClick(region)"
        class="map-region"
      />
    </svg>
    <div v-if="selectedRegion" class="region-info">
      <h3>{{ selectedRegion.name }}</h3>
      <p>{{ selectedRegion.info }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedRegion: null,
      regions: [
        {
          name: "Region 1",
          d: "M100,100 L200,100 L200,200 L100,200 Z", // example SVG path data
          color: "#1f77b4",
          info: "Details about Region 1",
        },
        {
          name: "Region 2",
          d: "M300,100 L400,100 L400,200 L300,200 Z",
          color: "#ff7f0e",
          info: "Details about Region 2",
        },
      ],
    };
  },
  methods: {
  handleMapClick() {
    // Handle clicks outside regions to deselect
    this.selectedRegion = null;
  },
  handleRegionClick(region) {
    this.selectedRegion = region;
  },
}

};
</script>

<style scoped>
.map-container {
  position: relative;
  max-width: 600px;
  margin: auto;
}
.map-region {
  cursor: pointer;
  transition: fill 0.3s ease;
}
.map-region:hover {
  fill-opacity: 0.7;
}
.region-info {
  margin-top: 20px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
</style>
