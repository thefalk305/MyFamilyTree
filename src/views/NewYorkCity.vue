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
  <div id="newyorkcity">
    <MiniNav />
    <h1 align="center">New York City, New York</h1>
    <p align="center">
      Welcome to New York, N.Y., USA. New York was one of the many ports in America that
      the immigrants came to after leaving Europe.
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
