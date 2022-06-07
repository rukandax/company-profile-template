<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "HomeAbout",
  data() {
    return {
      aboutInfos: [
        {
          title: "Who we are",
          subtitle: "Technology Company",
          content:
            "Sed ut perspiciatis unde omnis iste natus sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo.",
        },
        {
          title: "What we do",
          subtitle: "Professional Brand Management",
          content:
            "Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem.",
        },
        {
          title: "How we do",
          subtitle: "Strategize, Design, Collaborate",
          content:
            "Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse sequam nihil molestiae consequatur.",
        },
      ],
      currentInfoIdx: 0,
    };
  },
  computed: {
    isAvailableNext(): boolean {
      return this.currentInfoIdx < this.aboutInfos.length - 1;
    },
    isAvailablePrev(): boolean {
      return this.currentInfoIdx > 0;
    },
  },
  methods: {
    nextInfo() {
      if (this.isAvailableNext) {
        this.currentInfoIdx++;
      }
    },
    prevInfo() {
      if (this.isAvailablePrev) {
        this.currentInfoIdx--;
      }
    },
  },
});
</script>

<template>
  <div id="about" class="about">
    <div class="container">
      <div
        v-for="(info, infoIdx) in aboutInfos"
        :key="`info-${infoIdx}`"
        class="about__item"
        :class="{ 'about__item--active': currentInfoIdx === infoIdx }"
      >
        <h2 class="subheading-36 subheading-36--blue">{{ info.title }}</h2>
        <h3>{{ info.subtitle }}</h3>
        <p>{{ info.content }}</p>
      </div>

      <div class="pagination">
        <div class="pagination__indicator">
          <span class="pagination__indicator__active">
            {{ `0${currentInfoIdx + 1}`.slice(-2) }}
          </span>
          <span class="pagination__indicator__separator"> / </span>
          <span class="pagination__indicator__total">
            {{ `0${aboutInfos.length}`.slice(-2) }}
          </span>
        </div>
        <div class="pagination__navigation">
          <div
            class="pagination__navigation__box"
            :class="{ 'pagination__navigation__box--blue': isAvailablePrev }"
            @click="prevInfo"
          >
            <img
              :src="`/UI/${isAvailablePrev ? 'white' : 'gray'}-left-arrow.png`"
              alt="Move to previous about information"
            />
          </div>
          <div
            class="pagination__navigation__box"
            :class="{ 'pagination__navigation__box--blue': isAvailableNext }"
            @click="nextInfo"
          >
            <img
              :src="`/UI/${isAvailableNext ? 'white' : 'gray'}-right-arrow.png`"
              alt="Move to next about information"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.about {
  .container {
    padding: 60px 40px 40px 40px;
  }
}

.about__item {
  display: none;

  &--active {
    display: block;
  }

  h2 {
    margin-bottom: 15px;
  }

  h3 {
    margin-bottom: 15px;
    color: #000;
    font-size: 18px;
    font-weight: 400;
  }

  p {
    min-height: 200px;
    font-size: 14px;
    font-weight: 400;
    margin-bottom: 20px;
  }
}

.pagination {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.pagination__navigation {
  display: flex;
  justify-content: center;
  align-items: center;
}

.pagination__indicator__active,
.pagination__indicator__separator {
  font-size: 24px;
  font-weight: 500;
}

.pagination__navigation__box {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #f1f1f1;
  padding: 10px 15px;

  &--blue {
    background-color: #1ba0e1;
  }
}

@media only screen and (min-width: 480px) {
  .about {
    .container {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
    }
  }
  .about__item {
    display: block;
    margin: 0 20px;

    p {
      min-height: unset;
    }
  }

  .pagination {
    display: none;
  }
}
</style>
