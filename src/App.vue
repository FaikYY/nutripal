<!-- TODO: Example todo comment -->
<!-- TODO: Create a for loop for each ingreditient nutrition response from the api and print everything -->
<!-- TODO: Seperate the widget for the search bar -->
<!-- TODO: Seperate the widget for the button -->
<!-- TODO: Seperate the widget for the nutrition response -->
<!-- TODO: Create a nutrition information container like the ones ona real food package for the nutrition responses -->
<!-- TODO: Create a function to calculate the daily intake percantage of a specific nutrition such as "protein %20 of daily intake" -->
<!-- TODO: Ask user weight, height and age to calculate their daily needs and give the percentage based on that information -->
<!-- TODO: Add user login and signup to store the user data -->
<!-- TODO: Focus on seperation of concerns and clean the code by simplifying the variables -->
<!-- TODO: Add a demo api call counter to prevent api key limit exhaustion -->

<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <MainPage />
    <!-- <p>The text in the search bar: {{ searchKey }}</p> -->
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
import MainPage from './components/MainPage.vue'
import axios from 'axios';
import { API_KEY } from './config.js';

export default {
  name: 'App',
  components: {
    MainPage
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

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

input {
  padding: 1rem;
  font-size: 1.5rem;
}

button {
  font-size: 1.5rem;
  border: .5px solid rgb(200, 200, 200);
  margin: 1rem;
  padding: 1rem;
}
</style>