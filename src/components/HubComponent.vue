<template>
  <v-container class="d-flex ga-12 w-100">
      <v-row class="w-100">
        <v-col class="">
          <ServiceComponent
            class="w-100"
            :name="'Wikipedia'"
            :imageUrl="'https://upload.wikimedia.org/wikipedia/commons/0/07/Wikipedia_logo_%28svg%29.svg'"
          ></ServiceComponent>
        </v-col>
        <v-col>
          <ServiceComponent
            class="w-100"
            :name="'Google'"
            :imageUrl="'https://upload.wikimedia.org/wikipedia/commons/0/07/Wikipedia_logo_%28svg%29.svg'"
          ></ServiceComponent>
        </v-col>
        <v-col>
          <ServiceComponent
            class="w-100"
            :name="'Wikipedia'"
            :imageUrl="'https://upload.wikimedia.org/wikipedia/commons/0/07/Wikipedia_logo_%28svg%29.svg'"
          ></ServiceComponent>
        </v-col>
      </v-row>
  </v-container>
  <v-container class="d-flex w-100">
      <v-row class="w-100">
        <v-col class="">
          <ServiceComponent
            class="w-100"
            :name="'Wikipedia'"
            :imageUrl="'https://upload.wikimedia.org/wikipedia/commons/0/07/Wikipedia_logo_%28svg%29.svg'"
          ></ServiceComponent>
        </v-col>
        <v-col>
          <ServiceComponent
            class="w-100"
            :name="'Wikipedia'"
            :imageUrl="'https://upload.wikimedia.org/wikipedia/commons/0/07/Wikipedia_logo_%28svg%29.svg'"
          ></ServiceComponent>
        </v-col>
        <v-col>
          <ServiceComponent
            class="w-100"
            :name="'Wikipedia'"
            :imageUrl="'https://upload.wikimedia.org/wikipedia/commons/0/07/Wikipedia_logo_%28svg%29.svg'"
          ></ServiceComponent>
        </v-col>
      </v-row>
  </v-container>
</template>

<script lang="ts" setup>
import ServiceComponent from "./ServiceComponente";
</script>

<style scoped>
</style>
