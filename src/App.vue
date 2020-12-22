<template>
  <div class="container">
    <div class="columns is-multiline">
      <div v-for="(pokemon, index) in responseData.results" :key="index" class="column is-4">
        <pokemon :name="pokemon.name" :url="pokemon.url" :index="index + 1" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Pokemon from "./components/Pokemon.vue";

export default {
  name: "App",
  components: {
    Pokemon,
  },
  data() {
    return {
      responseData: [],
    };
  },
  created: function () {
    axios
      .get("https://pokeapi.co/api/v2/pokemon?limit=100&offset=0")
      .then((response) => {
        this.responseData = response.data;
      });
  },
};
</script>

<style>
</style>
