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
    <MainPage />
  </div>
</template>

<script>
import MainPage from './components/MainPage.vue'

export default {
  name: 'App',
  components: {
    MainPage
  }
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