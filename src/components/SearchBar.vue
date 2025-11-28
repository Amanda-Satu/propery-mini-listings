<template>
  <input
    class="search"
    type="text"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
    placeholder="Search by title or location..."
  />
</template>

<script>
export default {
  props: ["modelValue"]
};
</script>bn

<style>
.search {
  width: 100%;
  padding: 12px;
  margin: 10px 0;
  border: 1px solid #aaa;
  border-radius: 6px;
}
</style>
