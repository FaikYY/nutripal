<template>
  <div class="MainPage">
    <img alt="Vue logo" src="../assets/logo.png">
    <h2>Try to Search A Food To See The Nutrition Facts</h2>
    <input id="searchBar" v-on:keydown.enter="searchNutrition()" v-model="searchKey"
      placeholder="1lb chicken breast, 2 oranges..." />
    <button @click="searchNutrition">Search</button>


    <NutritionFact :nutritionFact="selectedNutrition" v-if="selectedNutrition.length > 0" />

      <div class="nutrition-facts">
  <header>
    <h1>Nutrition Facts</h1>
    <p>Serving Size 1 cup (228g)</p>
    <p>Servings Per Container 2</p>
  </header>
  
  <div class="section">
    <p><strong>Amount Per Serving</strong></p>
  </div>
  
  <div class="section calories">
    <p><strong>Calories</strong> 250</p>
    <p>Calories from Fat 110</p>
  </div>
  
  <div class="divider"></div>
  
  <div class="section">
    <p class="percent daily">% Daily Value*</p>
    <div class="grid">
      <p><strong>Total Fat</strong> 12g</p>
      <p class="right">18%</p>
      <p class="indent"><strong>Saturated Fat</strong> 3g</p>
      <p class="right">15%</p>
      <p class="indent">Trans Fat 0g</p>
      <p><strong>Cholesterol</strong> 30mg</p>
      <p class="right">10%</p>
      <p><strong>Sodium</strong> 470mg</p>
      <p class="right">20%</p>
      <p><strong>Total Carbohydrate</strong> 31g</p>
      <p class="right">10%</p>
      <p class="indent"><strong>Dietary Fiber</strong> 0g</p>
      <p class="right">0%</p>
      <p class="indent"><strong>Sugars</strong> 5g</p>
      <p><strong>Protein</strong> 5g</p>
    </div>
  </div>
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
  font-size: var(--size-xl);
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

.nutrition-facts {
  font-family: Arial, sans-serif;
  width: 300px;
  border: 1px solid #333;
  padding: 15px;
}

header {
  text-align: center;
  border-bottom: 1px solid #333;
}

.section {
  padding: 10px 0;
}

.divider {
  border-bottom: 1px solid #333;
}

.calories {
  font-size: 1.2em;
  border-bottom: 1px solid #333;
}

.grid {
  display: grid;
  grid-template-columns: auto 1fr;
}

.percent.daily {
  font-size: .9em;
}

.right {
  text-align: right;
}

.indent {
  padding-left: 10px;
}

</style>
