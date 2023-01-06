<script setup lang="ts">
import { TcHeader, TcContainer, TcTextInput, TcButton } from "./components";
import moment from "moment";
</script>

<script lang="ts">
import { ref } from "vue";
let dateTimeText = ref(moment().format("YYYY-MM-DD HH:mm:ss"));
let unixTimestamp = ref(moment(dateTimeText.value).unix());

function dateTimeTextChanged() {
  let momenDateTime = moment(dateTimeText.value);
  if (momenDateTime.isValid()) {
    let value = momenDateTime.unix();
    if (value !== unixTimestamp.value) {
      unixTimestamp.value = value;
    }
  }
}

function unixTimestampChanged() {
  let momenDateTime = moment.unix(unixTimestamp.value);
  if (momenDateTime.isValid()) {
    let value = momenDateTime.format("YYYY-MM-DD HH:mm:ss");
    if (value !== dateTimeText.value) {
      dateTimeText.value = value;
    }
  }
}

function getMoment(): moment.Moment {
  return moment.unix(unixTimestamp.value);
}

function setMoment(value: moment.Moment) {
  unixTimestamp.value = value.unix();
  unixTimestampChanged();
}

function copyDateTimeText() {
  navigator.clipboard.writeText(dateTimeText.value);
}

function copyUnixTimestamp() {
  navigator.clipboard.writeText(unixTimestamp.value.toFixed());
}
</script>

<template>
  <TcHeader title="Timestamp Converter" />
  <TcContainer>
    <div style="display: flex">
      <div style="flex-grow: 1; margin-right: 1rem">
        <TcTextInput label="Date and time" @input="dateTimeTextChanged" v-model="dateTimeText" />
      </div>
      <div style="padding-top: 1rem">
        <TcButton kind="ghost" @click="copyDateTimeText">Copy</TcButton>
      </div>
    </div>
    <div style="display: flex">
      <div style="flex-grow: 1; margin-right: 1rem">
        <TcTextInput label="Unix timestamp" @input="unixTimestampChanged" v-model="unixTimestamp" />
      </div>
      <div style="padding-top: 1rem">
        <TcButton kind="ghost" @click="copyUnixTimestamp">Copy</TcButton>
      </div>
    </div>
    <div>
      <span style="line-height: 2.5rem; margin-right: 1rem;">Start of:</span>
      <TcButton @click="setMoment(getMoment().startOf('day'))">Day</TcButton>
      <TcButton @click="setMoment(getMoment().startOf('isoWeek'))">Week</TcButton>
      <TcButton @click="setMoment(getMoment().startOf('month'))">Month</TcButton>
      <TcButton @click="setMoment(getMoment().startOf('year'))">Year</TcButton>
    </div>
    <div>
      <span style="line-height: 2.5rem; margin-right: 1rem;">Add:</span>
      <TcButton @click="setMoment(getMoment().add(1, 'hour'))">+1 hour</TcButton>
      <TcButton @click="setMoment(getMoment().add(1, 'day'))">+1 day</TcButton>
      <TcButton @click="setMoment(getMoment().add(1, 'week'))">+1 week</TcButton>
      <TcButton @click="setMoment(getMoment().add(1, 'month'))">+1 month</TcButton>
      <TcButton @click="setMoment(getMoment().add(1, 'year'))">+1 year</TcButton>
    </div>
    <div>
      <span style="line-height: 2.5rem; margin-right: 1rem;">End of:</span>
      <TcButton kind="secondary" @click="setMoment(getMoment().endOf('day'))">Day</TcButton>
      <TcButton kind="secondary" @click="setMoment(getMoment().endOf('isoWeek'))">Week</TcButton>
      <TcButton kind="secondary" @click="setMoment(getMoment().endOf('month'))">Month</TcButton>
      <TcButton kind="secondary" @click="setMoment(getMoment().endOf('year'))">Year</TcButton>
    </div>
    <div>
      <span style="line-height: 2.5rem; margin-right: 1rem;">Subtract:</span>
      <TcButton kind="secondary" @click="setMoment(getMoment().subtract(1, 'hour'))">+1 hour</TcButton>
      <TcButton kind="secondary" @click="setMoment(getMoment().subtract(1, 'day'))">+1 day</TcButton>
      <TcButton kind="secondary" @click="setMoment(getMoment().subtract(1, 'week'))">+1 week</TcButton>
      <TcButton kind="secondary" @click="setMoment(getMoment().subtract(1, 'month'))">+1 month</TcButton>
      <TcButton kind="secondary" @click="setMoment(getMoment().subtract(1, 'year'))">+1 year</TcButton>
    </div>
  </TcContainer>
</template>

<style scoped>
h1 {
  margin: 0;
  padding: 0;
  height: 2rem;
  font-size: 1rem;
  line-height: 2rem;
}
</style>
