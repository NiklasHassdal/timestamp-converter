<script setup lang="ts">
interface ButtonProps {
  kind?: "primary" | "secondary" | "ghost";
  animate?: boolean;
}

withDefaults(defineProps<ButtonProps>(), {
  kind: "primary",
});

defineEmits(["click"]);
</script>

<template>
  <button :class="{
    'tc-button': true,
    'tc-button-animate': animate,
    'tc-button-primary': kind === 'primary',
    'tc-button-secondary': kind === 'secondary',
    'tc-button-ghost': kind === 'ghost',
  }" v-bind="$attrs" @click="$emit('click')">
    <slot />
  </button>
</template>

<style scoped>
.tc-button {
  margin: 0.25rem 0.25rem 0 0;
  padding: 0.5rem 1rem;
  height: 2.5rem;
  border-radius: 4px;
  filter: drop-shadow(0px 0px 2px #ccc);
  cursor: pointer;
  transition: 0.2s;
}

.tc-button:hover {
  filter: drop-shadow(0px 0px 4px #ccc);
}

.tc-button-primary {
  border: 1px solid #08f;
  background-color: #08f;
  color: #eee;
}

.tc-button-primary:hover {
  border: 1px solid #222;
  background-color: #06f;
  color: #fff;
}

.tc-button-secondary {
  border: 1px solid #f40;
  background-color: #f40;
  color: #eee;
}

.tc-button-secondary:hover {
  border: 1px solid #222;
  background-color: #f00;
  color: #fff;
}

.tc-button-ghost {
  border: 1px solid #bbb;
  background-color: #ccc;
  color: #000;
}

.tc-button-ghost:hover {
  border: 1px solid #888;
  background-color: #aaa;
  color: #000;
}

.tc-button-animate:focus {
  -webkit-animation: beat 0.2s;
  animation: beat 0.2s;
}

.tc-button-animate:active {
  -webkit-animation: none;
  animation: none;
}

@keyframes beat {
  0% {
    -webkit-transform: scale(1, 1);
    transform: scale(1, 1);
  }

  25% {
    -webkit-transform: scale(0.8, 0.8);
    transform: scale(0.8, 0.8);
  }

  100% {
    -webkit-transform: scale(1, 1);
    transform: scale(1, 1);
  }
}
</style>
