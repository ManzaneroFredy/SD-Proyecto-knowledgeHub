<template>
  <v-sheet rounded="lg" class="d-flex w-25 justify-center">
    <v-container>
        <v-row no-gutters>
          <v-col class="d-flex justify-center">
            <v-img
              :height="80"
              :src="props.imageUrl"
            ></v-img>
          </v-col>
        </v-row>
        <v-row no-gutters>
          <v-col class="d-flex justify-center">
            <h2 class="font-weight-black">{{ props.name }}</h2>
          </v-col>
      </v-row>
      <v-row no-gutters>
          <v-col class="d-flex justify-center">
            <v-btn
              density="compact"
              size="small"
              rounded="sm"
              height="35"
              color="#7986CB"
              >Usar este servicio
            </v-btn>
          </v-col>
      </v-row>
    </v-container>
  </v-sheet>
</template>

<script lang="ts" setup>
  import { defineProps } from "vue";

  const props = defineProps({
    name: {
      type: String,
      required: true,
    },
    imageUrl: {
      type: String,
      required: true,
    },
  })

</script>

<style scoped>
</style>
