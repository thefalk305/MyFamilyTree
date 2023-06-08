<script setup>
import { reactive, ref, watchEffect } from "vue";
import ImageContainer from "../components/ImageContainer.vue";
import Relatives from "../components/Relatives.vue";

import axios from "axios";

const props = defineProps({
  hideRelatives: Boolean,
});
var showRelatives = true;
if (props.hideRelatives) showRelatives = false;

var brothersData = ref([]);
var infoTable = ref([]);
infoTable.value = inject("infoTable");
for (var i = 0; i < 5; i++) {
  brothersData.value[i] = infoTable.value[i + 3];
}

// async function getProducts() {
//   try {
//     var response = await axios.get("http://localhost:5001/products");
//   } catch (err) {
//     console.log(err);
//   }
//   items = response.data;
//   infoTable.value = items;
//   // copy info from db table for five brothers
//   for (i = 0; i < 5; i++) {
//     brothersData.value[i] = items[i + 3];
//   }
// }
// getProducts();
</script>

<template>
  <!-- <div class="image-containers"> -->
  <!-- <div class="image-container" v-for="item in brothersData" :key="item.id"> -->
  <div v-for="item in brothersData" :key="item.id">
    <ImageContainer :recordData="item" />
    <!-- <ImageContainer :recordData="item" :infoTable="infoTable" /> -->

    <Relatives v-if="showRelatives" :recordData="item" :infoTable="infoTable" />
  </div>
  <!-- </div> -->
</template>

<style scoped>
.image-containers {
  background-color: rgb(218, 218, 90);
  display: flex;
  position: absolute;
  height: 900px;
  width: 100%;
  justify-content: center;

  /*
  border: solid black 5px;
  background-color: antiquewhite;
  opacity: 0.9;
  border-radius: 30px;*/
}

.container:hover {
  cursor: pointer;
}
</style>
