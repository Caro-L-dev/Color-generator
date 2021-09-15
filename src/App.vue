<script>
import GlobalGenerator from "./components/GlobalGenerator.vue";

export default {
  name: "App",
  components: {
    GlobalGenerator,
  },
};
</script>

<template>
  <main>
    <global-generator />
  </main>
</template>

<style lang="scss">
@import "./assets/scss/_variables";

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: sans-serif;
}

body {
  background: $light-color;
}

main {
  margin: 0 auto;
  padding: 4rem 2rem;
}

button,
input {
  appearance: none;
  border: none;
  outline: none;
  background: none;
  color: inherit;
}

button {
  cursor: pointer;
}
</style>
