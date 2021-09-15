<script>
import ColorListGenerator from "./ColorListGenerator.vue";

export default {
  components: {
    ColorListGenerator,
  },
};
</script>

<template>
  <h4>Generator</h4>
  <div class="grid">
    <color-list-generator />
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

h4 {
  color: $grey-color;
  text-transform: uppercase;
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);

  @media (min-width: $small-device) {
    grid-template-columns: repeat(2, 1fr);
  }

  @media (min-width: $large-device) {
    grid-template-columns: repeat(4, 1fr);
  }
}
</style>
