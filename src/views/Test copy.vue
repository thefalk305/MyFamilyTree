<script setup>
import { reactive, ref, watchEffect } from "vue";
import SkeuomorphicToggleSwitch from "@/components/SkeuomorphicToggleSwitch.vue";
const square = document.querySelector(".square");
const circle = document.querySelector(".circle");
const btnHideSquare = document.querySelector(".btn-hide-square");
const btnPulseCircle = document.querySelector(".btn-pulse-circle");
</script>

<template>
  <div id="cross-fade">
    <SkeuomorphicToggleSwitch />
    <h1>hello</h1>
    <img class="bottom" src="@/assets/graphics/white.png" />
    <img class="top" src="@/assets/graphics/black.png" />
  </div>
</template>

<style scoped>
#cross-fade {
  position: relative;
  width: 200px;
  height: 200px;
  border: solid;
}
#cross-fade img {
  position: absolute;
}

.top {
  animation-name: fade;
  animation-timing-function: ease-in-out;
  animation-iteration-count: infinite;
  animation-duration: 4s;
  animation-direction: alternate;
}

@keyframes fade {
  0% {
    opacity: 1;
  }
  25% {
    opacity: 1;
  }
  75% {
    opacity: 0;
  }
  100% {
    opacity: 0;
  }
}
</style>
