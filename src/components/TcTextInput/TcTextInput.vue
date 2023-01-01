<script lang="ts">
export default {
  props: ["modelValue", "label", "id"],
  emits: ["update:modelValue"],
};
</script>

<template>
  <label v-if="label" class="tc-text-label">{{ label }}</label>
  <input
    class="tc-text-input"
    type="text"
    :value="modelValue"
    @input="$emit('update:modelValue', ($event as any).target.value)"
  />
</template>

<style scoped>
.tc-text-input {
  display: block;
  margin: 0.25rem 0 0.5rem 0;
  padding: 0.5rem;
  width: 100%;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 1rem;
  background-color: #fff;
  outline: none;
  filter: drop-shadow(0px 0px 2px #ccc);
  transition: 0.2s;
}

.tc-text-input:hover,
.tc-text-input:focus {
  border: 1px solid #888;
  filter: drop-shadow(0px 0px 4px #ccc);
}

.tc-text-label {
  display: block;
  margin: 0;
  padding: 0;
  font-size: 0.75rem;
}
</style>
