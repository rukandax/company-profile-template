<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "HomeSpeciality",
  data() {
    return {
      slider: [
        {
          image: "/UI/exhaust.png",
          content:
            "Slide 1 --- Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis euismod libero vel leo auctor, in venenatis nulla consequat. Sed commodo nunc sit amet congue aliquam.",
        },
        {
          image: "/UI/speed-improvement.png",
          content:
            "Slide 2 --- Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis euismod libero vel leo auctor, in venenatis nulla consequat. Sed commodo nunc sit amet congue aliquam.",
        },
        {
          image: "/UI/accesories.png",
          content:
            "Slide 3 --- Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis euismod libero vel leo auctor, in venenatis nulla consequat. Sed commodo nunc sit amet congue aliquam.",
        },
      ],
      sliderIndex: 1,
    };
  },
  computed: {
    isAvailableNext(): boolean {
      return this.sliderIndex < this.slider.length - 1;
    },
    isAvailablePrev(): boolean {
      return this.sliderIndex > 0;
    },
    defineSlideContent(): string {
      return this.slider[this.sliderIndex].content;
    },
  },
  methods: {
    changeSlide(index: number) {
      this.sliderIndex = index;
      let indexTranslateX;

      switch (this.sliderIndex) {
        case 0:
          indexTranslateX = 120;
          break;
        case 1:
          indexTranslateX = 0;
          break;
        case 2:
          indexTranslateX = -120;
          break;
      }

      const sliderImage = this.$refs["slider-image"] as HTMLElement;
      sliderImage.style.transform = `translateX(${indexTranslateX}px)`;
    },
    prevSlide() {
      if (this.isAvailablePrev) {
        this.sliderIndex--;
        this.changeSlide(this.sliderIndex);
      }
    },
    nextSlide() {
      if (this.isAvailableNext) {
        this.sliderIndex++;
        this.changeSlide(this.sliderIndex);
      }
    },
  },
});
</script>

<template>
  <div id="speciality" class="speciality">
    <div class="speciality-content">
      <div class="speciality-summary">
        <h2 class="subheading-24 subheading-24--blue">OUR SPECIALITY</h2>
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis euismod
          libero vel leo auctor, in venenatis nulla consequat. Sed commodo nunc
          sit amet congue aliquam.
        </p>
      </div>
      <div class="speciality-slider">
        <div class="speciality-slider__image" ref="slider-image">
          <img
            v-for="(slide, slideIdx) in slider"
            :key="`slide-${slideIdx}`"
            :src="slide.image"
            :alt="slide.content"
            :class="{ active: sliderIndex === slideIdx }"
          />
        </div>
        <div class="speciality-slider__description">
          {{ defineSlideContent }}
        </div>
        <p
          v-for="(slide, slideIdx) in slider"
          :key="`slide-${slideIdx}`"
          class="speciality-slider__description__each"
        >
          {{ slide.content }}
        </p>
        <div class="speciality-slider__navigation">
          <div @click="prevSlide">
            <img
              :src="`/UI/${isAvailablePrev ? 'blue' : 'gray'}-left-arrow.png`"
              alt="Move to next speciality"
            />
          </div>
          <div class="speciality-slider__navigation__dot">
            <div
              v-for="(_, slideIdx) in slider"
              :key="`slider-indicator-${slideIdx}`"
              @click="changeSlide(slideIdx)"
            >
              <img
                :src="`/UI/${slideIdx === sliderIndex ? 'active-' : ''}dot.png`"
                :alt="`Move to ${slideIdx} speciality`"
              />
            </div>
          </div>
          <div @click="nextSlide">
            <img
              :src="`/UI/${isAvailableNext ? 'blue' : 'gray'}-right-arrow.png`"
              alt="Move to next speciality"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.speciality {
  background-color: #509fdd;
  padding: 30px 20px;
}

.speciality-content {
  background-color: #fff;
  color: #303030;
  padding: 20px 20px 40px 20px;
}

h2 {
  margin-bottom: 20px;
}

.speciality-slider {
  overflow: hidden;
  margin-top: 40px;
}

.speciality-slider__image {
  position: relative;
  margin-bottom: 40px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  transform: translateX(0);
  transition: all 0.5s;

  img {
    width: 120px;
    transition: all 0.5s;
    scale: 0.5;

    &.active {
      transition: all 0.5s;
      scale: 1;
    }
  }
}

.speciality-slider__description {
  color: #a7a7a7;
  text-align: center;
}

.speciality-slider__description__each {
  display: none;
  margin-bottom: 20px;
}

.speciality-slider__navigation {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 40px;
}

.speciality-slider__navigation__dot {
  display: flex;
  justify-content: center;
  align-items: center;

  img {
    margin: 0 10px;
  }
}

@media only screen and (min-width: 480px) {
  .speciality-content {
    max-width: 1200px;
    box-sizing: border-box;
    padding: 40px;
    margin: auto;
    display: flex;
    justify-content: space-between;
    flex-direction: row-reverse;
  }

  .speciality-summary {
    text-align: right;
  }

  .speciality-slider__description {
    display: none;
  }

  .speciality-slider__description__each {
    display: block;
  }

  .subheading-24 {
    font-size: 36px;
    margin-top: 40px;
  }

  .speciality-slider__image {
    img {
      scale: 1;
    }
  }

  .speciality-slider__navigation {
    display: none;
  }
}
</style>
