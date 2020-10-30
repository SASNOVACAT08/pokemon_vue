<template>
  <div>
    <ul class="flex flex-col">
      <li
        class="flex flex-col content-center"
        v-for="(pokemon, index) in selection"
        :key="index"
      >
        <pokemon-card :pokemon="pokemon"></pokemon-card>
        <base-button
          @click="deletePokemon(index)"
          text="Retirer de l'équipe"
        ></base-button>
      </li>
    </ul>
  </div>
</template>

<script>
import PokemonCard from "./PokemonCard";
export default {
  name: "my-team",
  props: ["selection"],
  components: {
    PokemonCard
  },
  methods: {
    deletePokemon(index) {
      this.$emit("delete", index);
    }
  }
};
</script>
