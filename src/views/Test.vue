<script setup>
import { ref } from "vue";
import GoBack from "../components/GoBack.vue";
import BackToTop from "@/components/BackToTop.vue";
import MiniNav from "@/components/MiniNav.vue";
import Stone from "@/components/Stone.vue";

const images = []; // create array to hold image filenames

var dir = "@/assets/img/headstones";
var headstonesDir = require.context("@/assets/img/headstones", true, /^.*\.*$/);
let keys = headstonesDir.keys();
var headstones = keys.map(headstonesDir);
var newstones = [];
headstones = headstones.filter((stone) => {
  return stone.search("stone") < 0;
});

headstones.forEach(getImages);
// search for files with an image extension (jpg|jpeg|png|gif|svg)
function getImages(image) {
  if (image.search(/.(jpg|jpeg|png|gif|svg)$/i) > 0) {
    var image = image.split("/img")[1];
    var ext = "." + image.split(".")[2];
    image = image.split(".")[0];
    image = image.split("/")[1] + ext;
    images.push(image); // push image onto the array
  }
}
</script>

<template>
  <div id="headstones">
    <MiniNav />
    <h1 align="center">Head Stones &amp; Grave Markers</h1>

    <p align="center">(Can you identify them?)</p>
    <p>
      Below you will find several pictures of head stones, or grave markers if you prefer.
      Each one a little bit out of focus. Your task is to pick the right name with the
      right head stone... Three misses and you'll have to start over... Good Luck..
    </p>
    <p>&nbsp;</p>
    <hr />

    <div class="grid-container">
      <div v-for="(stone, { index }) in images" :key="index">
        <Stone :stone="stone" />
      </div>
    </div>
    <p align="center">
      <GoBack />
    </p>
  </div>
  <BackToTop />
</template>

<style scoped>
p {
  text-indent: 24px;
}
.grid-container {
  display: grid;
  grid-template-columns: auto auto auto;
  gap: 10px;
  background-color: beige;
  padding: 10px;
  height: fit-content;
}
</style>
