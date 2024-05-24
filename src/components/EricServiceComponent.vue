<template>
  <div class="ServiceHeader">
    <h1 class="title">Eric</h1>
    <v-container>
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-row>
          <v-col cols="12" md="6" v-for="(field, index) in fields" :key="index">
            <h3>{{ field.label }}</h3>
            <v-text-field
              v-model="field.value"
              :label="field.label"
              :rules="field.rules"
              required
            ></v-text-field>
          </v-col>
        </v-row>
        <v-btn :disabled="!valid" @click="submitForm">Submit</v-btn>
      </v-form>
      <EricServiceResultsComponent v-if="showResults" :results="fields" />
    </v-container>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue';
import EricServiceResultsComponent from './EricServiceResultsComponent.vue'

const valid = ref(false);
const showResults = ref(false);

const fields = reactive([
  { label: 'Field 1aca', value: '', rules: [(v) => !!v || 'Field 1 is required'] },
  { label: 'Field 2', value: '', rules: [(v) => !!v || 'Field 2 is required'] },
  { label: 'Field 1', value: '', rules: [(v) => !!v || 'Field 1 is required'] },
  { label: 'Field 2', value: '', rules: [(v) => !!v || 'Field 2 is required'] },
  { label: 'Field 1', value: '', rules: [(v) => !!v || 'Field 1 is required'] },
  { label: 'Field 2', value: '', rules: [(v) => !!v || 'Field 2 is required'] },
]);

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
</style>
