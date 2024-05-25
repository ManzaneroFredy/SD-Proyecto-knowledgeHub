<template>
  <div class="ServiceHeader">
    <h1 class="title">Google Académico</h1>
    <v-container>
      <v-form ref="form" v-model="valid" lazy-validation @submit.prevent="submitForm">
        <v-row>
          <v-col cols="12" md="6">
            <h3>Introduce una palabra</h3>
            <v-text-field
              v-model="query"
              label="Introduce una palabra"
              :rules="[rules.required]"
              required
            ></v-text-field>
          </v-col>
        </v-row>
        <v-btn type="submit" :disabled="!valid">Submit</v-btn>
      </v-form>
      <div v-if="showResults" class="related-searches">
        <div v-for="(search, index) in relatedSearches" :key="index" class="search-item">
          <h3>{{ search.query }}</h3>
          <p><a :href="search.link">{{ search.link }}</a></p>
        </div>
      </div>
    </v-container>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const valid = ref(false);
const showResults = ref(false);
const query = ref('');
const rules = {
  required: v => !!v || 'El campo es obligatorio'
};

const relatedSearches = [
  {
    query: "hola kola",
    link: "https://scholar.google.com/scholar?hl=en&as_sdt=0,33&qsp=1&q=hola+kola&qst=ib"
  },
  {
    query: "vpn hola",
    link: "https://scholar.google.com/scholar?hl=en&as_sdt=0,33&qsp=2&q=vpn+hola&qst=ib"
  },
  {
    query: "hola mohalla",
    link: "https://scholar.google.com/scholar?hl=en&as_sdt=0,33&qsp=3&q=hola+mohalla&qst=ib"
  },
  {
    query: "hola latin america",
    link: "https://scholar.google.com/scholar?hl=en&as_sdt=0,33&qsp=4&q=hola+latin+america&qst=ib"
  },
  {
    query: "hola hoop",
    link: "https://scholar.google.com/scholar?hl=en&as_sdt=0,33&qsp=5&q=hola+hoop&qst=ib"
  },
  {
    query: "lubica hola",
    link: "https://scholar.google.com/scholar?hl=en&as_sdt=0,33&qsp=6&q=lubica+hola&qst=ib"
  },
  {
    query: "hola loan act",
    link: "https://scholar.google.com/scholar?hl=en&as_sdt=0,33&qsp=7&q=hola+loan+act&qst=ib"
  },
  {
    query: "hola home owners loan",
    link: "https://scholar.google.com/scholar?hl=en&as_sdt=0,33&qsp=8&q=hola+home+owners+loan&qst=ib"
  }
];

const submitForm = () => {
  if (valid.value) {
    showResults.value = true;
  }
};
</script>

<style scoped>
.title{
  text-align: center;
}
.ServiceHeader{
  padding-top: 50px;
}

.related-searches {
  margin-top: 20px;
}

.search-item {
  margin-bottom: 10px;
}
</style>
