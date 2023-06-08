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
  <div id="arbra">
    <MiniNav />
    <h1 align="center">Arbrå, Sweden</h1>
    <p>
      Welcome to Arbrå, Sweden. It is here that Corine Noren was born and from here she
      left to come to Amerika. (More to follow)
    </p>
    <p align="center">
      <GoBack />
    </p>
  </div>
  <BackToTop />
</template>
