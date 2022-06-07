<script lang="ts">
import { defineComponent } from "vue";

import HomeBanner from "@/components/HomePage/HomeBanner.vue";
import HomeAbout from "@/components/HomePage/HomeAbout.vue";
import HomeCoreValue from "@/components/HomePage/HomeCoreValue.vue";
import HomeSpeciality from "@/components/HomePage/HomeSpeciality.vue";

export default defineComponent({
  name: "HomePage",
  components: {
    HomeBanner,
    HomeAbout,
    HomeCoreValue,
    HomeSpeciality,
  },
});
</script>

<template>
  <div>
    <HomeBanner />
    <HomeAbout />
    <HomeCoreValue />
    <HomeSpeciality />
  </div>
</template>
