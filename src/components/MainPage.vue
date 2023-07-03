<template>
  <div class="MainPage">
    <img alt="Vue logo" src="../assets/logo.png">
    <h2>Search Something</h2>
    <input id="searchBar" v-on:keydown.enter="searchNutrition()" v-model="searchKey"
      placeholder="Search for a nutrition..." />
    <button @click="searchNutrition">Search</button>


    <NutritionFact :nutritionFact="selectedNutrition" v-if="selectedNutrition.length > 0" />
  </div>
</template>

<script>

import axios from 'axios';
import { API_KEY } from '../config.js';
import NutritionFact from './NutritionFact.vue';

export default {
  components: { NutritionFact },
  props: {
    msg: String
  },
  data() {
    return {
      searchKey: '',
      selectedNutrition: [],
    }
  },
  methods: {
    searchNutrition() {
      const query = this.searchKey;

      axios
        .get('https://api.calorieninjas.com/v1/nutrition/', {
          params: { query },
          headers: { 'X-Api-Key': API_KEY },
        })
        .then((response) => {
          const items = response.data.items;
          console.log(items);
          if (items.length > 0) {
            const foundNutrition = items;
            console.log('Nutrition:', foundNutrition[0]);
            console.log('Name:', foundNutrition[0].name);
            console.log('Calories:', foundNutrition[0].calories);
            console.log('Protein:', foundNutrition[0].protein_g);
            console.log('Fat:', foundNutrition[0].fat_total_g);

            this.selectedNutrition = foundNutrition;

          } else {
            this.clearNutrition();
            console.log('No nutrition data found for the given query.');
            alert('No nutrition data found for the given query.');
          }
        })
        .catch((error) => {
          console.error('Error:', error.response.data);
          alert('Error:', error.response.data);
        });
      this.isFocused = false;
    },
    clearNutrition() {
      this.selectedNutrition = [];
    }
  },
}
</script>

<style scoped>
.MainPage {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 95vh;
}

.centered {
  width: 70%;
  text-align: center;
}

img {
  width: 40%;
  max-width: 200px;
}

h2 {
  color: var(--color-primary);
}

#searchBar {
  width: 70%;
  max-width: 600px;
  padding: var(--size-s);
  font-size: var(--font-size-l);
  color: rgb(125, 125, 125);
  background-color: var(--color-gray);
  border-radius: var(--size-s);
  border: .15rem solid rgb(200, 200, 200);
}

#searchBar::placeholder {
  color: rgb(125, 125, 125);
}

#searchBar:focus {
  outline: none;
  border-color: var(--color-primary-xlight);
}

button {
  font-size: var(--font-size-l);
  font-weight: 600;
  color: var(--color-primary-light);
  background-color: var(--color-gray);
  border: .15rem solid rgb(200, 200, 200);
  border-radius: .5rem;
  margin: 1rem;
  padding: var(--size-s);
  padding-left: var(--size-xl);
  padding-right: var(--size-xl);
}
</style>
