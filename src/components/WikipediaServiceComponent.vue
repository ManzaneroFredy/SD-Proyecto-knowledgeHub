<template>
  <div class="ServiceHeader">
    <h1 class="title">Wikipedia Service</h1>
    <v-container>
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-row>
          <v-col cols="12" md="6" v-for="(field, index) in fields" :key="index">
            <h3>{{ field.label }}</h3>
            <v-text-field
              v-model="query"
              :label="field.label"
              :rules="field.rules"
              required
            ></v-text-field>
          </v-col>
        </v-row>
        <v-btn :disabled="!valid" @click="submitForm">Submit</v-btn>
      </v-form>
      <WikipediaServiceResultsComponent v-if="showResults" :titleResults="queryResults.titles" :linkResults="queryResults.labels" />
    </v-container>
  </div>
</template>

<script setup>
import { ref, reactive} from 'vue';
import WikipediaServiceResultsComponent from './WikipediaServiceResultsComponent.vue';

const valid = ref(false);
const showResults = ref(false);
let query = ref("");
let queryResults = ref({
  titles : ref([]),
  labels : ref([])
  });

const fields = reactive([
  { label: 'Termino a buscar', value: '', rules: [(v) => !!v || 'Field 1 is required'] },
]);

const submitForm = async () => {
  await fetchArticles();
  showResults.value = true;
}

const fetchArticles = async () => {
  const proxyUrl = 'https://cors-anywhere.herokuapp.com/';
  const targetUrl = `https://es.wikipedia.org/w/api.php?action=opensearch&search=${encodeURIComponent(query.value)}&limit=10&namespace=0&format=json`;
  const url = proxyUrl + targetUrl;
  const RESPONSE_TITLES = 1;
  const RESPONSE_LINKS = 3;




  try {
    const response = await fetch(url)
    const data = await response.json();

    for (let key in data[RESPONSE_TITLES]) {
      queryResults.value.titles.push(data[RESPONSE_TITLES][key]);
    }

    for (let key in data[RESPONSE_LINKS]) {
      queryResults.value.labels.push(data[RESPONSE_LINKS][key]);
    }
  } catch (error) {
    console.error('Error fetching books', error)
  }

}

</script>

<style scoped>
.title{
  text-align: center;
}
.ServiceHeader{
  padding-top: 50px;
}
</style>
