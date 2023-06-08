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
  <div class="transportation">
    <MiniNav />
    <h1 align="center">S.S. Norden</h1>
    <p align="center">
      The Norden is the ship that Karin Noren traveled on from G�teborg to Hamburg,
      Germany
    </p>
    <p align="center">
      <img border="0" src="@/assets/img/SSNorden.jpg" width="865" height="545" />
    </p>
    <p align="center">SS Norden from G�teborg, Sweden to Hamburg, Germany.</p>
    <p align="center">
      <GoBack />
    </p>
  </div>
  <BackToTop />
</template>
