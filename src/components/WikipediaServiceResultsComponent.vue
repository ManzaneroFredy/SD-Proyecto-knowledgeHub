<template>
  <v-container>
    <v-row>
      <v-col cols="12" v-for="(titleResults, index) in props.titleResults" :key="index">
        <h3>{{ titleResults }}</h3>
        <p>{{ props.linkResults.at(index) }}</p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  titleResults: {
    type: Array,
    required: true,
  },
  linkResults: {
    type: Array,
    required: true,
  }
});
</script>

<style scoped>
</style>
