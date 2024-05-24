<template>
  <v-container>
    <v-row>
      <v-col cols="12" v-for="(field, index) in results" :key="index">
        <h3>{{ field.label }}</h3>
        <p>{{ field.value }}</p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  results: {
    type: Array,
    required: true,
    validator: (value) => {
      return value.every(item => typeof item.label === 'string' && typeof item.value === 'string');
    }
  }
});
</script>

<style scoped>
</style>
