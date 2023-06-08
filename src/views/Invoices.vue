<template>
  <div>
    <GoBack />

    <h1>Invoices</h1>
  </div>
</template>

<script>
import GoBack from "../components/GoBack.vue";

import { onBeforeRouteLeave } from "vue-router";
export default {
  setup() {
    onBeforeRouteLeave((to, from) => {
      const answer = window.confirm(
        "Are you sure you want to leave?  Invoices are super awesome!"
      );
      if (!answer) return false;
    });
  },
};
</script>

<style scoped>
h1 {
  position: absolute;
  top: 0px;
  left: 300px;
}
</style>
