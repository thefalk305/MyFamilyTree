<script setup>
import Modal from "./Modal.vue";
import { ref } from "vue";
import InfoPage from "@/views/InfoPage.vue";

const props = defineProps({
  recordData: Object,
});

const showInfoPage = ref(false);

$(document).ready(function () {
  var images = [];
  images = $("img");
  var i = 1;
});
</script>

<template>
  <div @click="showInfoPage = true">
    <img :src="require('@/assets/img/' + recordData.pic)" alt="photo" />
    <p style="font-size: 20px" >{{ recordData.name }}</p>
  </div>

  <Teleport to="body" :disabled="false">
    <!-- use the modal component, pass in the prop -->
    <InfoPage :show="showInfoPage" @close="showInfoPage = false" :id="recordData.id">
    </InfoPage>
  </Teleport>
</template>

<style scoped>
.modal-button:hover {
  scale: 1.1;
  background-color: rgba(167, 253, 167, 0.9);
  border-radius: 10px;
}
</style>
