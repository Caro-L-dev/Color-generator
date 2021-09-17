<script>
export default {
  data() {
    return {
      color: '',
    }
  },
  created: function() {
    this.getRandomColor();

    document.addEventListener('keydown', press => {
      if(press.code === 'Space') this.getRandomColor();
    });
  },
  watch: {
    color: function(displayRandomColor) {
      document.body.style.backgroundColor = displayRandomColor;
      // document.getElementById("colorId").style.backgroundColor= displayRandomColor;
    }
  },
  methods: {
    getRandomColor: function() {
      this.color = '#' + (Math.random().toString(16) + "000000").substring(2,8);
    },
    copyHexColorValue: function() {
      document.execCommand("copy");
    }
  }
};
</script>

<template>
  <main>
      <h1 class="title">Color Generator</h1>
      <p class="subtitle"> Press [
          <button class="generator-btn" v-on:click="$emit('color-item-change', getRandomColor())">Space</button>]
           to generate a new color palette.
      </p>
      <h4 class='title-two'>Generator</h4>
      <div class="grid__color-item">
          <div class="color-item">
            <input type="text" class="color-item__hex-color-value" :value='color' />
            <button class="copy__hex-color-value"
              v-on:click="$emit('color-item__copied', copyHexColorValue())"
            >
              Copy
            </button>
          </div>

        </div>
  </main>
</template>

<style lang="scss">
@import "./assets/scss/_variables";
@import "./assets/scss/_global";

.title {
  color: $dark-color;
  font-size: 2.5rem;
  font-weight: 900;
  text-transform: uppercase;
  margin-bottom: 1rem;
}

.subtitle {
    color: $grey-color;
    font-size: 1.125rem;
    margin-bottom: 2rem;
}

.generator-btn {
    color: $primary-color;
    font-size: inherit;
    font-weight: 700;
    background: linear-gradient(to bottom right, $primary-color, $secondary-color);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    transition: 0.4s ease-in-out;

    &:hover {
        padding-left: 0.5rem;
        padding-right: 0.5rem;
    }
}

.title-two {
  color: $grey-color;
  text-transform: uppercase;
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.grid__color-item {
  display: grid;
  grid-template-columns: repeat(1, 1fr);

  @media (min-width: $small-device) {
    grid-template-columns: repeat(2, 1fr);
  }

  @media (min-width: $large-device) {
    grid-template-columns: repeat(4, 1fr);
  }
}

.color-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0.5rem 1rem;
    border-radius: 1rem;
    margin: 0.3rem;
    color: #fff;
    background-color: $dark-color;
    transition: 0.4s ease-out;
    border: 0.2rem solid transparent;

    &__hex-color-value {
      text-align: center;
    }

    &__copied {
      border-color: red;
    }
}

@media (min-width: $small-device) {
  .h1 {
    font-size: 4rem;
  }
}

@media (min-width: $large-device) {
  .color-item {
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .color-item__hex-color-value {
    margin-top: 1rem;
    margin-bottom: 1rem;
  }
}
</style>
