<template>
  <a v-if="isExternal" :href="to" rel="noopener" class="external-link" target="_blank"
    ><slot
  /></a>
  <router-link v-else :="$props" class="internal-links"><slot /> </router-link>
</template>

<script>
import { RouterLink } from "vue-router";
export default {
  props: {
    ...RouterLink.props,
  },
  computed: {
    isExternal() {
      return typeof this.to === "string" && this.to.startsWith("http");
    },
  },
};
</script>

<style scoped>
a:hover {
  background-color: rgb(0, 128, 100);
}
</style>
