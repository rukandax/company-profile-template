<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "DefaultHeader",
  data() {
    return {
      isShowNavItem: false,
    };
  },
});
</script>

<template>
  <div class="header">
    <div class="container">
      <div>
        <a href="#">
          <img src="/company-logo.png" alt="Company Logo" />
        </a>
      </div>
      <div class="navigation-item" :class="{ displayed: isShowNavItem }">
        <a href="#about" @click="isShowNavItem = false">Who We Are</a>
        <a href="#core-value" @click="isShowNavItem = false">Our Values</a>
        <a href="#speciality" @click="isShowNavItem = false">The Perks</a>
      </div>
      <div class="navigation-button" @click="isShowNavItem = !isShowNavItem">
        <img src="/UI/burger-menu.png" alt="Show menu" />
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.header {
  .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 30px;
    position: relative;
  }
}

.navigation-item {
  z-index: 10;
  display: none;
  position: absolute;
  bottom: -115px;
  left: 0;
  right: 0;
  background-color: #777;

  &.displayed {
    display: block;
  }

  a {
    display: block;
    color: #fff;
    text-decoration: none;
    padding: 10px 20px;
    border-bottom: 1px solid #333;
  }
}

@media only screen and (min-width: 480px) {
  .navigation-item {
    position: unset;
    display: flex;
    justify-content: space-between;
    align-items: center;
    bottom: unset;
    left: unset;
    right: unset;
    background-color: unset;

    a {
      color: #333;
      border-bottom: unset;
    }
  }

  .navigation-button {
    display: none;
  }
}
</style>
