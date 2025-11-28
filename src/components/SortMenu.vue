<template>
  <select
    class="sort"
    :value="modelValue"
    @change="$emit('update:modelValue', $event.target.value)"
  >
    <option disabled value="">Sort by price</option>
    <option value="low">Low → High</option>
    <option value="high">High → Low</option>
  </select>
</template>

<script>
export default {
  props: ["modelValue"]
};
</script>

<style>
.sort {
  width: 100%;
  padding: 10px;
  margin-bottom: 15px;
  border-radius: 6px;
  border: 1px solid #aaa;
}
</style>