<script>
export default {
    name: 'BtnGenerator',
    methods: {
        changeColor: function() {
            return '#' + Math.floor(Math.random() * 6777215).toString(16);
        }
    }
};
</script>


<template>
    <p>
        Press [
        <button
            class="generator-btn"
            v-on:click="$emit('background-change', changeColor())">
            Space
        </button>
        ] to generate a new color palette.
    </p>
</template>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

p {
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
</style>
