<template>
  <div class="ServiceHeader">
    <h1 class="title">Google Books</h1>
    <v-container>
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-row>
          <v-col cols="12" md="6">
            <h3>Introduce el título</h3>
            <v-text-field
              v-model="title"
              label="Introduce el título"
              :rules="[rules.required]"
              required
            ></v-text-field>
          </v-col>
        </v-row>
        <v-btn :disabled="!valid" @click="submitForm">Submit</v-btn>
      </v-form>
      <GoogleBooksServiceResultsComponent v-if="showResults" :results="transformedResults" />
    </v-container>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import GoogleBooksServiceResultsComponent from './GoogleBooksServiceResultsComponent';

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
  const apiKey = "AIzaSyDXQDfS8hLzJiOqhUaARycLfxluD7y3zWY";
  const url = `https://www.googleapis.com/books/v1/volumes?q=${encodeURIComponent(query)}&key=${apiKey}`;

  try {
    const response = await fetch(url);
    const data = await response.json();
    results.value = data.items || [];
  } catch (error) {
    console.error('Error fetching books:', error);
  }
};

const transformedResults = computed(() => {
  return results.value.map(book => ({
    label: book.volumeInfo.title,
    value: book.volumeInfo.authors ? book.volumeInfo.authors.join(', ') : 'Unknown author',
    //previewLink: book.previewLink || 'No preview available',
  }));
});
</script>

<style scoped>
.title {
  text-align: center;
}
.ServiceHeader {
  padding-top: 50px;
}
</style>
