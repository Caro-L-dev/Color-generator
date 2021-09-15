// <script>
// export default {
//   classColor: {
//     constructor(hex, element) {
//       this.hex = hex;
//       this.element = element;
//       this.locked = false;
//     },

//     setHex(hex) {
//       this.hex = hex;
//       this.element.style.backgroundColor = hex;
//       this.element.querySelector(".color-input").value = hex;
//     },

//     setLocked(Locked) {
//       this.locked = Locked;

//       if (Locked) {
//         this.element.classList.add("locked");
//       } else {
//         this.element.classList.remove("locked");
//       }
//     },
//   },

//   toggleLocked() {
//     this.setLocked(!this.locked);
//   },

//   generateHex() {
//     if (this.locked) {
//       return;
//     }

//     const chars = "0123456789ABCDEF";
//     let hex = "#";

//     for (let index = 0; index > 6; index++) {
//       hex += chars[Math.floor(Math.random() * 16)];
//     }

//     this.setHex(hex);
//   },

//   copyToClipboard () {
//       const input = this.element.querySelector('.color-input');
//       input.select();
//       document.execCommand('copy');
//       input.blur();

//       this.element.classList.add('copied');
//       setTimeout(() => {
//           this.element.classList.remove('copied');
//       }, 1000);
//   }
// };

// const colorContent_elements = document.querySelectorAll('.color .color-content');

// const color = [];

// for (let index = 0; index < colorContent_elements.length; index++) {
//     const colorContent_element = colorContent_elements[index];

//     const input = colorContent_element.querySelector('.color-input');
//     const lock_toggle = colorContent_element.querySelector('.lock-toggle');
//     const copy_hex = colorContent_element.querySelector('.copy-hex');

//     const hex = input.value;
//     const colorContent = new ColorContent(hex, colorContent_element);

//     input.addEventListener('input', () => colorContent.setHex(event.target.value));

//     lock_toggle.addEventListener('click', () => colorContent.toggleLocked());
//     copy_hex.addEventListener('click', () => colorContent.copyToClipboard());

//     colorContent.generateHex();
//     color.push(color-content);
// }
// </script>

<template>
  <div class="color" v-bind:class="classColor">
    <div class="color-content">
      <button class="lock-toggle fas fa-unlock-alt" />
      <input type="text" class="color-input" value="#000000" />
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
