<template>
  <div>
    <p class="text-center">Il y a {{ pokedex.length }} Pokemons</p>
    <ul class="flex flex-col">
      <li class="flex flex-col" v-for="pokemon in goodPage" :key="pokemon.id">
        <pokemon-card :pokemon="pokemon"></pokemon-card>
        <base-button
          @click="seeDetails(pokemon)"
          text="Voir les détails"
        ></base-button>
        <base-button
          @click="addSelection(pokemon)"
          text="Ajouter à l'équipe"
        ></base-button>
      </li>
    </ul>
    <ul class="mt-5 flex flex-wrap">
      <li class="mx-3" v-for="index in numberPages" :key="index">
        <p :class="{ 'font-bold': page === index }" @click="changePage(index)">
          {{ index }}
        </p>
      </li>
    </ul>
  </div>
</template>

<script>
import pokedex from "../assets/data/pokedex.json";
import PokemonCard from "./PokemonCard";

export default {
  name: "pokemon-list",
  components: {
    PokemonCard
  },
  data() {
    return {
      pokedex,
      page: 1
    };
  },
  methods: {
    seeDetails(pokemon) {
      this.$emit("details", pokemon);
    },
    addSelection(pokemon) {
      this.$emit("selection", pokemon);
    },
    changePage(pageNumber) {
      this.page = pageNumber;
    }
  },
  computed: {
    goodPage() {
      let pokemons = [];
      this.pokedex.forEach((pokemon, index) => {
        if ((this.page - 1) * 10 <= index && this.page * 10 > index) {
          pokemons.push(pokemon);
        }
      });
      return pokemons;
    },
    numberPages() {
      return Math.ceil(this.pokedex.length / 10);
    }
  }
};
</script>
