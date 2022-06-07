<script lang="ts">
import { defineComponent } from "vue";
import { RouterView } from "vue-router";

import DefaultHeader from "./components/DefaultHeader.vue";
import DefaultFooter from "./components/DefaultFooter.vue";

export default defineComponent({
  name: "App",
  components: {
    RouterView,
    DefaultHeader,
    DefaultFooter,
  },
});
</script>

<template>
  <DefaultHeader />
  <RouterView />
  <DefaultFooter />
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Rubik:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");

$blue: #029fe4;

html {
  scroll-behavior: smooth;
}

body {
  font-family: Rubik;
  margin: 0;
  padding: 0;
  color: #777777;
}

.container {
  max-width: 1200px;
  margin: auto;
  box-sizing: border-box;
}

p {
  margin: 0;
}

h1 {
  margin: 0;
}

h2 {
  margin: 0;

  &.subheading-24 {
    font-size: 24px;
    margin: 0;

    &--blue {
      color: $blue;
    }
  }

  &.subheading-36 {
    font-size: 36px;
    margin: 0;

    &--blue {
      color: $blue;
    }
  }
}

h3 {
  margin: 0;
}

.vector-layer-1,
.vector-layer-2 {
  background-position: bottom;
  background-size: contain;
  background-repeat: no-repeat;
}

@media only screen and (min-width: 480px) {
  .vector-layer-1,
  .vector-layer-2 {
    background-size: cover;
    background-position: 0 70px;
  }
}
</style>
