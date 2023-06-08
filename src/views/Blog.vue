<script>
import GoBack from "../components/GoBack.vue";
import BackToTop from "@/components/BackToTop.vue";
import MiniNav from "@/components/MiniNav.vue";

export default {
  components: {
    GoBack,
    BackToTop,
    MiniNav,
  },
};
</script>

<template>
  <div id="blogContainer">
    <MiniNav />
    <h1 align="center">Falkman's Family Blog is under construction.</h1>
    <p align="center">
      <GoBack />
    </p>
  </div>
  <BackToTop />
</template>

<style scoped>
#blogContainer {
  width: 100%;
  height: 300px;
}
</style>
