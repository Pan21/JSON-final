
//Template Layout for the divs that hold the Imported content from the JSON file
<template>
<div>
    <button v-on:click="submit">Load game Data</button>
    <div v-for="gameData in gameDataList" :key="gameData.id" class="games-data">
    <div class="games-stats">

    <div class="games-icon">
        <img :src="`${ gameData.logo }`">
      </div>

      <div class="textContain">
      
      <div class="contentContain">
      <h1>Useful Facts about {{gameData.developer}}</h1>

      <div class="gamesListed">
        <h1>Notable games by {{gameData.Developer}}</h1>
        <div>
          <ul>
          <li>{{ gameData.nameOne }}</li>
          <li>{{ gameData.games.nameTwo }}</li>
          <li>{{ gameData.games.nameThree }}</li>
          <li>{{ gameData.games.nameFour }}</li>
          </ul>
        </div>
      
      </div>

      <p>{{gameData.developer}} was established in the year {{gameData.year}}</p>
      
      <p>Their headquarters is located in {{gameData.location}}</p>
      </div>

      </div>
        <div>
        </div>
      </div>
  </div>
  </div>
</template>

//Used to fetch the JSON data needed to populate the Template Above
<script>

    // collection of all Imports needed to properly Run the Loading animation

    import Vue from 'vue';
    // Import component
    import Loading from 'vue-loading-overlay';
    // Import stylesheet
    import 'vue-loading-overlay/dist/vue-loading.css';
    // Init plugin
    Vue.use(Loading);

// Makes the connection to the JSON file
export default {
  name: "games",
  data() {
    return {
      gameDataList: []
    };
  },
  methods: {

    // Base method used to intiate the file collection from the JSon
    getGamesData() {
      fetch("data.json")
        .then(response => response.json())
        .then(data => (this.gameDataList = data));
    },
            // ON click loading tool with a spinning icon to "load" the data
            submit() {
                let loader = this.$loading.show({
                });

                // Simulates a loading time then calls data at the end.
                setTimeout(() => {
                  loader.hide()
                  
                },3000)     
                // Calls the Loading function after the Set loading delay
                this.getGamesData()            
            },                      
  }
};
</script>

//Styling for the Content template

<style>


.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
.games-data {
  opacity: 100;
  
  width: 30%;
  display: flex;
  margin: 0 auto;
  background-color: lightgray;
  
  border: 10px solid black;
  padding: 20px;
  margin-bottom: 20px;

}

.gamesListed{
  

}

.textContain{
margin: 0 auto;
width: 80%;
height: 400px;
display: block;
}

.games-icon {
  flex-grow: 3;
  justify-content: center;
}

.games-stats {
  flex-grow: 8;

  margin: 0 auto;
}

.textContain:hover {
  .gamesListed{
    display:block;
  }
  .textContain{
    display:none;
  }
}

img {
  width:40%;
  border-radius: 100px;
  .img:hover{
  width:20%;
  background-color:red;
  }
}

button {
    padding:10px;
    background-color: #1aa832;
    color: white;
    border: 1px solid #ccc;
}
</style>