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
  <div id="albany">
    <MiniNav />
    <h1 align="center">Albany, New York</h1>
    <p>
      Albany, N.Y. is the start of another branch of the family. This one being Herman's
      wife, Mary. (Herman is Nil's oldest son). It is Mary's folks that come from Albany.
      (More to follow)
    </p>
    <p align="center">
      <GoBack />
    </p>
  </div>
  <BackToTop />
</template>
