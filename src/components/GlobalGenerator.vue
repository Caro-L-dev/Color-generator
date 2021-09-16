<script>
import HeaderGenerator from "./HeaderGenerator.vue";
import BtnGenerator from "./BtnGenerator.vue";
import Generator from "./Generator.vue";

export default {
  name: "GlobalGenerator",
  components: {
    HeaderGenerator,
    BtnGenerator,
    Generator,
  },
};
</script>

<template>
  <header-generator />
  <btn-generator />
  <generator />
</template>
