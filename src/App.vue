<template>
  <div class="container">

    <HeaderBar :total="filteredProperties.length" />

    <SearchBar v-model="searchQuery" />
    <SortMenu v-model="sortOrder" />

    <div class="grid">
      <PropertyCard
        v-for="p in filteredProperties"
        :key="p.id"
        :property="p"
        @bookmark="toggleBookmark"
      />
    </div>

  </div>
</template>

<script>
import propertiesData from "./data/properties";
import HeaderBar from "./components/HeaderBar.vue";
import SearchBar from "./components/SearchBar.vue";
import SortMenu from "./components/SortMenu.vue";
import PropertyCard from "./components/PropertyCard.vue";

export default {
  components: { HeaderBar, SearchBar, SortMenu, PropertyCard },

  data() {
    return {
      properties: propertiesData,
      searchQuery: "",
      sortOrder: ""
    };
  },

  computed: {
    filteredProperties() {
      let results = this.properties.filter((p) =>
        p.title.toLowerCase().includes(this.searchQuery.toLowerCase()) ||
        p.location.toLowerCase().includes(this.searchQuery.toLowerCase())
      );

      if (this.sortOrder === "low") {
        results.sort((a, b) => a.price - b.price);
      }
      if (this.sortOrder === "high") {
        results.sort((a, b) => b.price - a.price);
      }

      return results;
    }
  },

  methods: {
    toggleBookmark(id) {
      const item = this.properties.find((p) => p.id === id);
      item.bookmarked = !item.bookmarked;
    }
  }
};
</script>

<style>
.container {
  max-width: 800px;
  margin: auto;
  padding: 20px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
  gap: 20px;
}
</style>
