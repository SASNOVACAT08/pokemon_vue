<template>
  <nav-bar :selected="selected" @navigate="selectComponent"></nav-bar>
  <div class="mx-auto max-w-screen-lg p-4">
    <selection-list class="mb-2" :selection="selection"></selection-list>
    <component
      :is="selected"
      :pokemon="pokemon"
      :selection="selection"
      @details="goToDetails"
      @selection="addSelection"
      @delete="deletePokemon"
    ></component>
  </div>
</template>

<script>
import SelectionList from "./components/SelectionList";
import PokemonList from "./components/PokemonList";
import PokemonDetails from "./components/PokemonDetails";
import MyTeam from "./components/MyTeam";
import NavBar from "./components/navigation/NavBar";

export default {
  name: "App",
  components: {
    SelectionList,
    PokemonList,
    PokemonDetails,
    MyTeam,
    NavBar
  },
  data() {
    return {
      selected: "pokemon-list",
      pokemon: null,
      selection: []
    };
  },
  methods: {
    goToDetails(pokemon) {
      this.pokemon = pokemon;
      this.selected = "pokemon-details";
    },
    addSelection(pokemon) {
      if (this.selection.length < 6) {
        this.selection.push(pokemon);
      }
    },
    selectComponent(component) {
      this.selected = component;
    },
    deletePokemon(index) {
      this.selection.splice(index, 1);
    }
  }
};
</script>
