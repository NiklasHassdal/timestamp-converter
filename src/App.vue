<script setup lang="ts">
import { TcHeader, TcContainer, TcTextInput, TcButton } from "./components";
import moment from "moment";
</script>

<script lang="ts">
export default {
  data() {
    return {
      inputValue: "test input value",
      test: 1,
    };
  },
  components: { TcButton },
};
</script>

<template>
  <TcHeader title="Timestamp Converter" />
  <TcContainer>
    <TcTextInput label="This is an input field" v-model="inputValue" />
    Input value: {{ moment(inputValue).format("YYYY-MM-DD HH:mm:ss") }}<br />
    <TcButton @click="test++">Test button</TcButton>
    <TcButton kind="secondary" @click="test++">Test button</TcButton>
    <TcButton kind="ghost" @click="test++">Test button</TcButton>
    {{ test }}
  </TcContainer>
</template>
