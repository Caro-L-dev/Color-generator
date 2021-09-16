<script>
export default {
  name: 'ColorGenerator',
  props: {
    colorProps: String
  },
  data() {
    return {
      value: '#000000',
      color: this.colorProps
    }

  },
  created: function() {
    this.changeColor();

    document.addEventListener('keydown', event => {
      if(event.code === 'Space')this.changeColor();
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
    backgroundChange: function(newColor) {
      this.color = newColor;
    }

    }
};

</script>


<template>
  <div class="color" v-bind:color="color">
    <div class="color-content">
      <button class="lock-toggle fas fa-unlock-alt" />
      <input type="text" class="color-input" value={{color}} />
      <button class="copy-hex">Copy</button>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

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
  h1 {
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
