<script setup lang="ts">
import { TcHeader, TcContainer, TcTextInput } from "./components";
</script>

<script lang="ts">
export default {
  data() {
    return {
      inputValue: "test input value",
    };
  },
};
</script>

<template>
  <TcHeader title="Timestamp Converter" />
  <TcContainer>
    <TcTextInput label="This is an input field" v-model="inputValue" />
    Input value: {{ inputValue }}
  </TcContainer>
</template>
