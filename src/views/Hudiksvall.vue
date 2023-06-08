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
  <div id="hudiksvall">
    <MiniNav />
    <h1 align="center">Hudiksvall, Sweden</h1>
    <p>
      Welcome to Hudiksvall, Sweden. It is from here that Nils P. Falkman left to come to
      Amerika.
    </p>
    <p align="center">
      <GoBack />
    </p>
  </div>
  <BackToTop />
</template>
