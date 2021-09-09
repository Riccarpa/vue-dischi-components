<template>
  <div id="app">
    <Header />
    <DiscSection />
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import DiscSection from "@/components/DiscSection.vue";

export default {
  name: "App",
  components: {
    Header,
    DiscSection,
  },
};
</script>

<style lang="scss">
@import "./scss/style.scss";
</style>
