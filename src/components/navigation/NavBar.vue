<template>
  <ul class="flex justify-center m-4">
    <li class="m-2" v-for="(nav, index) in navigation" :key="index">
      <p
        :class="{ 'font-bold': nav.component === selected }"
        @click="selectComponent(nav.component)"
      >
        {{ nav.text }}
      </p>
    </li>
  </ul>
</template>

<script>
export default {
  name: "nav-bar",
  props: ["selected"],
  data() {
    return {
      navigation: [
        { text: "Liste de tous les pokémons", component: "pokemon-list" },
        { text: "Mon équipe", component: "my-team" }
      ]
    };
  },
  methods: {
    selectComponent(component) {
      this.$emit("navigate", component);
    }
  }
};
</script>
