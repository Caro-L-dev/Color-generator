<script>
import HeaderGenerator from "./HeaderGenerator.vue";
import SubtitleGenerator from "./SubtitleGenerator.vue";
import Generator from "./Generator.vue";

export default {
  name: "GlobalGenerator",
  components: {
    HeaderGenerator,
    SubtitleGenerator,
    Generator,
  },
};
</script>

<template>
  <header-generator />
  <subtitle-generator />
  <generator />
</template>
