<template>
  <div class="card">
    <img :src="property.image" alt="" />

    <div class="info">
      <h3>{{ property.title }}</h3>
      <p>{{ property.location }}</p>

      <p class="price">R {{ property.price }}</p>
      <p class="type">{{ property.type }}</p>

      <span v-if="!property.available" class="badge">Not Available</span>

      <button class="bookmark" @click="$emit('bookmark', property.id)">
        {{ property.bookmarked ? '★ Bookmarked' : '☆ Bookmark' }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["property"]
};
</script>

<style>
.card {
  background: #2e2e2e;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}

.card img {
  width: 100%;
  height: 170px;
  object-fit: cover;
}

.info {
  padding: 12px;
}

.price {
  font-weight: bold;
}

.badge {
  display: inline-block;
  background: #c0392b;
  color: white;
  padding: 5px 10px;
  border-radius: 6px;
  font-size: 12px;
  margin-top: 8px;
}

.bookmark {
  margin-top: 10px;
  background: #1e1e2f;
  color: white;
  border: none;
  padding: 8px 12px;
  border-radius: 6px;
  cursor: pointer;
}
</style>
