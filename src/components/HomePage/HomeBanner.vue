<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "HomeBanner",
});
</script>

<template>
  <div class="banner">
    <div class="vector-layer-1">
      <div class="vector-layer-2">
        <div class="container">
          <div class="banner-content">
            <h1>Discover<br />Your Wonder</h1>
            <p>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
              eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut
              enim ad minim veniam.
            </p>
            <div class="slide-down">
              <a href="#about">
                <img src="/UI/slide-down.png" alt="Go to next section" />
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.banner {
  background-image: url("/banner-benjamin-wong-4-ka5rdCesI-unsplash.png");
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

.vector-layer-1 {
  background-image: url("/banner-vector-1.svg");
}

.vector-layer-2 {
  background-image: url("/banner-vector-2.svg");
}

.banner-content {
  position: relative;
  color: #fff;
  padding: 300px 40px 90px 40px;

  h1 {
    font-weight: 500;
    font-size: 36px;
    margin: 0 0 16px 0;
  }

  p {
    font-size: 16px;
  }
}

.slide-down {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  position: absolute;
  bottom: -20px;
  left: calc(50vw - 20px);
  background-color: #fff;
  padding: 10px;
  border-radius: 50%;
  box-shadow: 0 0 1px 1px #e8e8e8;
}

@media only screen and (min-width: 480px) {
  .banner-content {
    h1 {
      font-size: 72px;
    }
  }
  .slide-down {
    display: none;
  }
}
</style>
