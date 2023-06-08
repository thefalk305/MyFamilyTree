<script setup>
import { ref } from "vue";
import GoBack from "../components/GoBack.vue";
import BackToTop from "@/components/BackToTop.vue";
import MiniNav from "@/components/MiniNav.vue";

function reblur(e) {
  var regex = /\d+/g;
  var blurValue = 1;
  var image = e.target.parentNode.childNodes[0];
  var blur = image.style.filter;
  if (blur != "none") {
    var blurValue = parseInt(blur.match(regex)[0]);
  }
  if (blurValue > 0) {
    e.target.innerHTML === "blur" ? blurValue++ : blurValue--;
    var blurString = "blur(" + blurValue + "px)";
    image.style.filter = blurString;
  } else {
    image.style.filter = "none";
  }

  console.log(blurValue);
}
</script>

<template>
  <div id="temp">
    <MiniNav />
    <h1 align="center">Head Stones &amp; Grave Markers</h1>

    <p align="center">(Can you identify them?)</p>
    <p>
      Below you will find several pictures of head stones, or grave markers if you prefer.
      Each one a little bit out of focus. Your task is to pick the right name with the
      right head stone... Three misses and you'll have to start over... Good Luck..
    </p>
    <p>&nbsp;</p>
    <div class="grid-container">
      <div>
        <img id="ts1" src="@/assets/img/headstones/stone-1r.jpg" style="filter: blur(5px)" alt="hs9" />
        <button @click="reblur">blur</button>
        <button @click="reblur">deblur</button>
      </div>
      <div>
        <img src="@/assets/img/headstones/stone-2r.jpg" style="filter: blur(5px)" alt="hs9" />
        <button @click="reblur">blur</button>
        <button @click="reblur">deblur</button>
      </div>
      <div>
        <img @click="ts3 = !ts3" src="@/assets/img/headstones/stone-3r.jpg" style="filter: blur(5px)" alt="hs9" />
        <button @click="reblur">blur</button>
        <button @click="reblur">deblur</button>
      </div>

      <div>
        <img src="@/assets/img/headstones/stone-4r.jpg" style="filter: blur(5px)" alt="hs9" />
        <button @click="reblur">blur</button>
        <button @click="reblur">deblur</button>
      </div>
      <div>
        <img src="@/assets/img/headstones/stone-5r.jpg" style="filter: blur(5px)" alt="hs9" />
        <button @click="reblur">blur</button>
        <button @click="reblur">deblur</button>
      </div>
      <div>
        <img src="@/assets/img/headstones/stone-6r.jpg" style="filter: blur(5px)" alt="hs9" />
        <button @click="reblur">blur</button>
        <button @click="reblur">deblur</button>
      </div>

      <div>
        <img src="@/assets/img/headstones/stone-7r.jpg" style="filter: blur(5px)" alt="hs9" />
        <button @click="reblur">blur</button>
        <button @click="reblur">deblur</button>
      </div>
      <div>
        <img src="@/assets/img/headstones/stone-8r.jpg" style="filter: blur(5px)" alt="hs9" />
        <button @click="reblur">blur</button>
        <button @click="reblur">deblur</button>
      </div>
      <div>
        <img src="@/assets/img/headstones/stone-9r.jpg" style="filter: blur(5px)" alt="hs9" />
        <p>
          &nbsp;
          <button @click="reblur">blur</button>
          <button @click="reblur">deblur</button>
        </p>
      </div>
    </div>
    <p align="center">
      <GoBack />
    </p>
  </div>
  <BackToTop />
</template>

<style scoped>
div {
  width: 100%;
  height: 286px;
  vertical-align: top;
  align-content: right;
  padding: 20px;
}

img {
  align-content: center;
  width: 278px;
  height: 154px;
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
