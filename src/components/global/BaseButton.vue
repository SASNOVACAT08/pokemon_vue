<template>
  <button class="rounded border p-2">{{ text }}</button>
</template>
<script>
export default {
  name: "base-button",
  props: ["text"]
};
</script>
