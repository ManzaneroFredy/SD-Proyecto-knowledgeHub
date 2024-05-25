<template>
  <div class="ServiceHeader">
    <h1 class="title">Google Académico</h1>
    <v-container>
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-row>
          <v-col cols="12" md="6">
            <h3>Introduce una palabra</h3>
            <v-text-field
              v-model="title"
              label="Introduce una palabra"
              :rules="[rules.required]"
              required
            ></v-text-field>
          </v-col>
        </v-row>
        <v-btn :disabled="!valid" @click="submitForm">Submit</v-btn>
      </v-form>
      <GoogleAcademicServiceResultsComponent v-if="showResults" :results="transformedResults" />
    </v-container>
  </div>
</template>
<script setup>
import { ref, computed } from 'vue';
import GoogleAcademicServiceResultsComponent from './GoogleAcademicServiceResultsComponent';

const valid = ref(false);
const showResults = ref(false);
const title = ref('');
const results = ref([]);

const rules = {
  required: v => !!v || 'El campo es obligatorio'
};


const submitForm = async () => {
  if (valid.value) {
    await fetchBooks(title.value);
    showResults.value = true;
  }
};

const fetchBooks = async (query) => {
const apiKeycode = "5afd317774b45c647bf04cfad9c22b8326215620189e91165c49ec06fbf876c3";
const baseUrl = `https://serpapi.com/search.json?engine=google_scholar&q=${encodeURIComponent(query)}&apikey=${apiKeycode}`;
const proxyUrl = "https://cors-anywhere.herokuapp.com/"; // URL del proxy

const url = `${proxyUrl}${baseUrl}`;

  try {
    const response = await fetch(url, {
      headers: {
        'X-Requested-With': 'XMLHttpRequest'
      }
    });
    const data = await response.json();
    results.value = data.items || [];
  } catch (error) {
    console.error('Error fetching documents:', error);
  }
};

const transformedResults = computed(() => {
  return results.value.map(document => ({
    label: document.organic_results.title,
    value: document.organic_results.link,
  }));
});
</script>

<style scoped>
.title{
  text-align: center;
}
.ServiceHeader{
  padding-top: 50px;
}
</style>
