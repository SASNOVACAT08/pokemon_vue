<template>
  <div class="flex flex-col">
    <img
      class="w-1/4 mx-auto"
      :src="pokemonImageName"
      :alt="pokemon.name.french"
    />
    <h2 class="text-center font-bold">{{ pokemon.name.french }}</h2>
    <ul class="flex justify-center">
      <li class="mx-3" v-for="(type, index) in pokemon.type" :key="index">
        {{ type }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "pokemon-card",
  props: ["pokemon"],
  computed: {
    pokemonImageName() {
      if (this.pokemon.id.toString().length === 1) {
        return `/images/00${this.pokemon.id}.png`;
      } else if (this.pokemon.id.toString().length === 2) {
        return `/images/0${this.pokemon.id}.png`;
      }
      return `/images/${this.pokemon.id}.png`;
    }
  }
};
</script>
