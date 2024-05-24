<template>
  <div>
    <h1 class="title">Bienvenido a knowledgeHub</h1>
    <v-container class="d-flex ga-12 w-100">
      <v-row class="w-100">
        <v-col class="">
          <ServiceComponent
            class="w-100"
            name="Wikipedia"
            imageUrl="https://upload.wikimedia.org/wikipedia/commons/0/07/Wikipedia_logo_%28svg%29.svg"
            @click="showWikipediaService"
          ></ServiceComponent>
        </v-col>
        <v-col>
          <ServiceComponent
            class="w-100"
            name="Google Académico"
            imageUrl="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQAHiotweovbY-VYLheHXIjgJ1_USrBghmkldIrLDkELw&s"
          ></ServiceComponent>
        </v-col>
        <v-col>
          <ServiceComponent
            class="w-100"
            name="Google Books"
            imageUrl="https://i.blogs.es/c5141d/play-books/1366_2000.jpg"
          ></ServiceComponent>
        </v-col>
      </v-row>
    </v-container>
    <v-container class="d-flex w-100">
      <v-row class="w-100">
        <v-col class="">
          <ServiceComponent
            class="w-100"
            name="ERIC"
            imageUrl="https://upload.wikimedia.org/wikipedia/commons/5/5b/ERIC_logo_%28US_ED%29.png"
          ></ServiceComponent>
        </v-col>
        <v-col>
          <ServiceComponent
            class="w-100"
            name="WorldCat Search API (OCLC)"
            imageUrl="https://developer.api.oclc.org/assets/header-logo-DmMTs40y.png"
          ></ServiceComponent>
        </v-col>
        <v-col>
          <ServiceComponent
            class="w-100"
            name="EBSCOhost SOAP Web Service"
            imageUrl="https://minitex.umn.edu/sites/default/files/styles/manual_crop_16_9/public/images/2020-01/EBSCOhost_logo_CMYK%5B1%5D.png?h=1b4c7e77&itok=ujsGeW0Z"
          ></ServiceComponent>
        </v-col>
      </v-row>
    </v-container>
    <WikipediaServiceComponent v-if="showWikipedia" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ServiceComponent from './ServiceComponente.vue';
import WikipediaServiceComponent from './WikipediaServiceComponent.vue';

const showWikipedia = ref(false);

const showWikipediaService = () => {
  showWikipedia.value = true;
};
</script>

<style scoped>
.title {
  text-align: center;
}
</style>
