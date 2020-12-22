<template>
  <div class="card">
    <div class="card-image">
      <figure class="image is-4by3" v-if="pokemon.sprites">
        <img :src="pokemon.sprites.other.dream_world.front_default" alt="Placeholder image" />
      </figure>
    </div>
    <div class="card-content">
      <div class="media">
        <div class="media-content">
          <p class="title is-4">{{ capitalize(name) }}</p>
          <p class="subtitle is-6">
            <span
              class="tag"
              v-for="(type, index) in pokemon.types"
              :key="index"
              >{{ type.type.name }}</span
            >
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Pokemon",
  created: function () {
    axios.get(this.url).then((response) => {
      this.pokemon = response.data;
    });
  },
  data() {
    return {
      pokemon: {},
    };
  },
  props: {
    index: Number,
    name: String,
    url: String,
  },
  methods: {
    capitalize: (value) => {
      return value[0].toUpperCase() + value.slice(1);
    },
  },
};
</script>

<style scoped>
.tag {
  margin-right: 5px;
}
</style>
