<template>
  <div class="hello">
    <img alt="Vue logo" src="../assets/logo.png">
    <h1>Search Something</h1>
    <input v-model="searchKey" placeholder="search a nutrition..." />
    <button @click="makeAPICall">Search</button>
    <h2>Nutrition Name: {{ nutrition.name }}</h2>
    <h2>Serving Size: {{ nutrition.serving_size_g }}g</h2>
    <h2>Calories: {{ nutrition.calories }}</h2>
    <h2>Protein: {{ nutrition.protein_g }}g</h2>
    <h2>Fat: {{ nutrition.fat_total_g }}g</h2>
  </div>
</template>

<script>
import axios from 'axios';
import { API_KEY } from '../config.js';

export default {
  props: {
    msg: String
  },
  data() {
    return {
      searchKey: '',
      nutrition: {}
    }
  },
  methods: {
    makeAPICall() {
      const query = this.searchKey;

      axios
        .get('https://api.calorieninjas.com/v1/nutrition', {
          params: { query },
          headers: { 'X-Api-Key': API_KEY },
        })
        .then((response) => {
          const items = response.data.items;
          if (items.length > 0) {
            const nutrition = items[0]; // Assuming you only want the first item
            console.log('Nutrition:', nutrition);
            console.log('Name:', nutrition.name);
            console.log('Calories:', nutrition.calories);
            console.log('Protein:', nutrition.protein_g);
            console.log('Fat:', nutrition.fat_total_g);

            this.nutrition = nutrition;
            // Print other nutrition values as needed
          } else {
            console.log('No nutrition data found for the given query.');
          }
        })
        .catch((error) => {
          console.error('Error:', error.response.data);
        });
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
