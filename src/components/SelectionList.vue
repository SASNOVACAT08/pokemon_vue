<template>
  <div>
    <p class="text-center">Il y {{ selection.length }}/6 dans l'équipe.</p>
  </div>
</template>

<script>
export default {
  name: "selection-list",
  props: ["selection"]
};
</script>
