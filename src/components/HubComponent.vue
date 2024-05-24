<template>
  <div>
    <h1 class="title">Bienvenido a knowledgeHub</h1>
    <v-container class="d-flex ga-12 w-100">
      <v-row class="w-100">
        <v-col>
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
            @click="showGoogleAcademicService"
          ></ServiceComponent>
        </v-col>
        <v-col>
          <ServiceComponent
            class="w-100"
            name="Google Books"
            imageUrl="https://i.blogs.es/c5141d/play-books/1366_2000.jpg"
            @click="showGoogleBooksService"
          ></ServiceComponent>
        </v-col>
      </v-row>
    </v-container>
    <v-container class="d-flex w-100">
      <v-row class="w-100">
        <v-col>
          <ServiceComponent
            class="w-100"
            name="ERIC"
            imageUrl="https://upload.wikimedia.org/wikipedia/commons/5/5b/ERIC_logo_%28US_ED%29.png"
            @click="showEricService"
          ></ServiceComponent>
        </v-col>
        <v-col>
          <ServiceComponent
            class="w-100"
            name="WorldCat Search API (OCLC)"
            imageUrl="https://developer.api.oclc.org/assets/header-logo-DmMTs40y.png"
            @click="showOclcService"
          ></ServiceComponent>
        </v-col>
        <v-col>
          <ServiceComponent
            class="w-100"
            name="EBSCOhost SOAP Web Service"
            imageUrl="https://minitex.umn.edu/sites/default/files/styles/manual_crop_16_9/public/images/2020-01/EBSCOhost_logo_CMYK%5B1%5D.png?h=1b4c7e77&itok=ujsGeW0Z"
            @click="showEbscoService"
          ></ServiceComponent>
        </v-col>
      </v-row>
    </v-container>
    <v-container>
      <v-row justify="center">
        <v-col>
          <ServiceComponent
            name="nowtes"
            imageUrl="https://cdn.discordapp.com/attachments/974116062473883688/1243652146033987665/LogoMakr.png?ex=665240d1&is=6650ef51&hm=7ed5cb14d8bfd7fa68fe3cb28c11303748135266d4f1bded8a8ab7180d95f839&"
          ></ServiceComponent>
        </v-col>
      </v-row>
    </v-container>
    <WikipediaServiceComponent v-if="showWikipedia"/>
    <GoogleAcademicServiceComponent v-if="showGoogleAcademic"/>
    <GoogleBooksServiceComponent v-if="showGoogleBooks"/>
    <EricServiceComponent v-if="showEric" />
    <OCLCServiceComponent v-if="showOclc" />
    <EBSCOServiceComponent v-if="showEbsco" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ServiceComponent from './ServiceComponente.vue';
import WikipediaServiceComponent from './WikipediaServiceComponent.vue';
import GoogleAcademicServiceComponent from './GoogleAcademicServiceComponent.vue';
import GoogleBooksServiceComponent from './GoogleBooksServiceComponent.vue';
import EricServiceComponent from './EricServiceComponent.vue';
import OCLCServiceComponent from './OCLCServiceComponent.vue';
import EBSCOServiceComponent from './EBSCOServiceComponent.vue';

const showWikipedia = ref(false);
const showGoogleAcademic = ref(false);
const showGoogleBooks = ref(false);
const showEric = ref(false);
const showOclc = ref(false);
const showEbsco = ref(false);

const hideServices = () => {
  showWikipedia.value = false;
  showGoogleAcademic.value = false;
  showGoogleBooks.value = false;
  showEric.value = false;
  showOclc.value = false;
  showEbsco.value = false;
}

const showWikipediaService = () => {
  hideServices();
  showWikipedia.value = true;
};

const showGoogleAcademicService = () => {
  hideServices();
  showGoogleAcademic.value = true;
};

const showGoogleBooksService = () => {
  hideServices();
  showGoogleBooks.value = true;
}

const showEricService = () => {
  hideServices();
  showEric.value = true;
}

const showOclcService = () => {
  hideServices();
  showOclc.value = true;
}

const showEbscoService = () => {
  hideServices();
  showEbsco.value = true;
}
</script>

<style scoped>
.title {
  text-align: center;
}
</style>
