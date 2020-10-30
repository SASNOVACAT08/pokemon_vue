<template>
  <div class="flex flex-col mt-4">
    <img
      class="w-1/2 mx-auto"
      :src="pokemonImageName"
      :alt="pokemon.name.french"
    />
    <h2 class="font-bold text-center m-2">{{ pokemon.name.french }}</h2>
    <h2 class="font-bold text-center m-2">{{ pokemon.name.english }}</h2>
    <h2 class="font-bold text-center m-2">{{ pokemon.name.japanese }}</h2>
    <ul class="flex justify-center">
      <li class="mx-3" v-for="(type, index) in pokemon.type" :key="index">
        {{ type }}
      </li>
    </ul>
    <div class="flex justify-center">
      <p class="mx-3">HP : {{ pokemon.base.HP }}</p>
      <p class="mx-3">Attack : {{ pokemon.base.Attack }}</p>
      <p class="mx-3">Defense : {{ pokemon.base.Defense }}</p>
    </div>
    <base-button
      @click="addSelection(pokemon)"
      text="Ajouter à l'équipe"
    ></base-button>
  </div>
</template>

<script>
export default {
  name: "pokemon-details",
  props: ["pokemon"],
  methods: {
    addSelection(pokemon) {
      this.$emit("selection", pokemon);
    }
  },
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
