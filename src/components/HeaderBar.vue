<template>
  <header class="header">
    <h1>Homes & Beyond</h1>
    <p>{{ total }} properties available</p>
  </header>
</template>

<script>
export default {
  props: {
    total: Number
  }
};
</script>

<style>
.header {
  padding: 20px;
  text-align: center;
  background: #1e1e2f;
  color: white;
}
</style>
