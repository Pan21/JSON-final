

//Sets the template for the base layer for the Content template to be injected into later.

<template>
  <div id="app">
    <games />
  </div>
</template>


//Pulls content from the Games.vue file to import into the app
<script>
import games from '../src/components/games'

export default {
  name: 'app',
  components: {
    games
  }
}
</script>

//Used to style the base layer of the program 
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
