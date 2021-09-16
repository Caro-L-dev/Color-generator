<script>
export default {
  data() {
    return {
      color: '',
      value: '',
    }
  },
  created: function() {
    this.changeColor();
    this.setColor();

      document.addEventListener('keydown', event => {
      if(event.code === 'Space') this.changeColor();
    });
  },
   watch: {
     color: function(value) {
     document.body.style.backgroundColor = value;
     }
   },
  methods: {
    changeColor: function() {
    this.color = '#' + Math.floor(Math.random() * 6777215).toString(16);
    },
    setColor: function(newColor) {
    this.$emit('setColor', newColor);
    }
  }
};
</script>

<template>
  <main>
      <h1 class="title">Color Generator</h1>
      <p class="subtitle">
         Press [
          <button
            class="generator-btn"
            v-on:click="$emit('color-content-change', changeColor())"
          >
          Space
          </button>]
           to generate a new color palette.
      </p>
      <h4 class='title-two'>Generator</h4>
      <div class="grid-color-box">

        <div class="color">
          <div class="color-content">
            <button class="lock-toggle fas fa-unlock-alt" />
            <input type="text" class="color-input" :value='color' />
            <button class="copy-hex">Copy</button>
          </div>
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

.grid-color-box {
  display: grid;
  grid-template-columns: repeat(1, 1fr);

  @media (min-width: $small-device) {
    grid-template-columns: repeat(2, 1fr);
  }

  @media (min-width: $large-device) {
    grid-template-columns: repeat(4, 1fr);
  }
}

.color {
  &-content {
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
  }

  &-input {
    text-align: center;
  }

  &-copied {
    border-color: red;
  }
}

.lock-toggle {
  opacity: 0.5;
  transition: 0.4s;

  &--is-locked {
    opacity: 1;
  }
}

@media (min-width: $small-device) {
  .h1 {
    font-size: 4rem;
  }
}

@media (min-width: $large-device) {
  .color-content {
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .color-input {
    margin-top: 1rem;
    margin-bottom: 1rem;
  }
}
</style>
