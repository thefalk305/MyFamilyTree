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
  <div id="bremen">
    <MiniNav />
    <h1 align="center">Bremen, Germany</h1>

    <p>
      Welcome to Bremen, Germany. Bremen was one of the many ports through which
      immigrants traveled on their way to American, Canada, and even Australia.
    </p>
    <p align="center">
      <GoBack />
    </p>
  </div>
  <BackToTop />
</template>

<style>
#hamburg {
  padding: 30px;
}
</style>
