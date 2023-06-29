<template>
  <div class="hello">
    <img alt="Vue logo" src="../assets/logo.png">
    <h1>Search Something</h1>
    <input v-model="searchKey" placeholder="Search for a nutrition..." />
    <button @click="searchNutrition">Search</button>


    <div class="centered" v-if="selectedNutrition.length > 0">
      <NutritionFact :nutritionFact="selectedNutrition" />
    </div>
    <div v-else>
      <!-- <p>No nutrition data found for the given query.</p> -->
    </div>
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
      selectedNutrition: []
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
    },
    clearNutrition() {
      this.selectedNutrition = [];
    }
  },
}
</script>

<style scoped>
.hello {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
}

.centered {
  width: 50%;
  text-align: center;
}

h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
