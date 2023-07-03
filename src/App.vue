<!-- TODO: Example todo comment -->
<!-- TODO: Seperate the widget for the search bar -->
<!-- TODO: Seperate the widget for the button -->
<!-- TODO: Create a nutrition information container like the ones ona real food package for the nutrition responses -->
<!-- TODO: Create a function to calculate the daily intake percantage of a specific nutrition such as "protein %20 of daily intake" -->
<!-- TODO: Ask user weight, height and age to calculate their daily needs and give the percentage based on that information -->
<!-- TODO: Add user login and signup to store the user data -->
<!-- TODO: Focus on seperation of concerns and clean the code by simplifying the variables -->
<!-- TODO: Add a demo api call counter to prevent api key limit exhaustion, specifically for live demo version -->
<!-- TODO: Save searched nutrition facts somewhere and keep track of them -->

<template>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <div id="app">
    <MainPage />
  </div>
</template>

<script>
import MainPage from './components/MainPage.vue';

export default {
  name: 'App',
  components: {
    MainPage
  }
};
</script>

<style>
@import url("../styles/material-you.css");
@import url("../styles/variables.css");

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.debug {
  outline: 5px dotted red;
}
</style>