<script>
import GoBack from "../components/GoBack.vue";
import PassengerList from "./PassengerList.vue";
import BackToTop from "@/components/BackToTop.vue";

export default {
  components: {
    GoBack,
    PassengerList,
    BackToTop,
  },
};
</script>

<template>
  <div id="liverpool">
    <MiniNav />
    <h1 align="center">Liverpool, England</h1>
    <p>
      Welcome to Liverpool, England. Liverpool was one of the many ports through which
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
