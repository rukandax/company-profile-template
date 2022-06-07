<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "HomeCoreValue",
  data() {
    return {
      coreValueDescs: [
        {
          title: "Our Core Values",
          content:
            "Nam libero tempore, cum soluta nobis est eligendi optio cumque nihil impedit quo minus id quod maxime placeat.",
        },
        {
          title: "Intellectual Honesty",
          content:
            "Itaque earum rerum hic tenetur a sapiente delectus, ut aut reiciendis voluptatibus maiores alias conse.",
        },
        {
          title: "Curiosity",
          content:
            "At vero eos et accusamus et iusto odio dignissimos ducimus qui blanditiis praesentium voluptatum deleniti atque.",
        },
      ],
    };
  },
});
</script>

<template>
  <div id="core-value" class="core-value">
    <div class="container">
      <div class="core-value__summary">
        <h2 class="subheading-36 subheading-36--blue">Our Core Values</h2>
        <p>
          Ridiculus laoreet libero pretium et, sit vel elementum convallis
          fames. Sit suspendisse etiam eget egestas. Aliquet odio et lectus
          etiam sit.<br /><br />In mauris rutrum ac ut volutpat, ornare nibh
          diam. Montes, vitae, nec amet enim.
        </p>
      </div>
      <div class="core-value__description">
        <div
          v-for="(item, itemIdx) in coreValueDescs"
          :key="`core-value-${itemIdx}`"
          class="core-value__description__item"
        >
          <h3>{{ item.title }}</h3>
          <p>{{ item.content }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.core-value {
  background-color: #f8f8f8;

  .container {
    padding: 40px 40px 350px 40px;
    background-image: url("/core-values-illustration.png");
    background-position: 0 100%;
    background-repeat: no-repeat;
  }
}

h2 {
  text-align: center;
  margin-bottom: 24px;
}

.core-value__summary {
  margin-bottom: 35px;
}

h3 {
  margin: 0;
  font-size: 24px;
  font-weight: 400;

  &::before {
    display: inline-block;
    content: "";
    border-top: 2px solid black;
    width: 30px;
    margin: 0 15px -10px 0;
    transform: translateY(-1rem);
  }
}

.core-value__description__item {
  margin-bottom: 25px;

  h3 {
    margin-bottom: 10px;
    color: #000;
  }
}

@media only screen and (min-width: 480px) {
  .core-value {
    .container {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      padding: 40px 40px 180px 40px;
    }
  }

  .core-value__summary {
    padding-right: 40px;
  }

  .core-value__description {
    padding-top: 60px;
  }
}
</style>
