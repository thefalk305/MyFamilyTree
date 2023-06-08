<script setup>
import { reactive, ref, watchEffect, inject } from "vue";
import GoBack from "@/components/GoBack.vue";
import BackToTop from "@/components/BackToTop.vue";
import MiniNav from "@/components/MiniNav.vue";
import Animation from "@/components/Animation.vue";

import Tree from "../components/Tree.vue";
import axios from "axios";
// import { readdir, readFile } from "fs/promises";
import FamilyPage from "@/views/FamilyPage.vue";

// get all image files from folder
var treePics = require.context("@/assets/treepics", true, /^.*\.*$/);
// console.log(treePics.keys());
let keys = treePics.keys();
var animationPics = keys.map(treePics);

let json = require("@/assets/infotable.json");
// console.log(json, "the json obj");
var images = [];

var brothersData = ref([]);
// console.log(infoTable.value);
var items = [];
var i;
var familyTree = ref([]);
var familyTreeLocs = ref([]);
var infoTable = ref([]);
infoTable.value = inject("infoTable");
// brother's id's = 4 thru 8
for (i = 0; i < 5; i++) {
  brothersData.value[i] = infoTable.value[i + 3];
}

// async function uniqueValues() {
//   const files = await readdir(filesDir);
//   const filesContent = await Promise.all(
//     files.map((file) => {
//       return readFile(filesDir + "/" + file, "utf8");
//     })
//   );
//   const arr = filesContent.reduce((acc, data) => {
//     acc.push(data.toString().split("\n"));
//     return acc;
//   }, []);

//   return new Set(arr);
// }

// uniqueValues().then((values) => {
//   console.log(values);
// });

familyTreeLocs.value = [
  [50, -350, 370],
  [196, -75, 370],
  [434, -580, 370],
  [434, 414, 370],
  [718, -1383, 470],
  [718, -460, 370],
  [718, 279, 370],
  [718, 1154, 470],
  [1000, -2000, 370],
  [1000, -1450, 370],
  [1052, -900, 370],
  [1052, -350, 370],
  [1002, 200, 370],
  [1002, 750, 370],
  [1052, 1300, 370],
  [1052, 1850, 370],
  [1286, -2635, 370],
  [1286, -2125, 370],
  [1356, -1605, 370],
  [1336, 1955, 370],
  [1336, 2485],
];

familyTree.value = [
  [0, [4, 5, 6, 7, 8]],
  [1, [2, 13]],
  [2, [17, 39]],
  [3, [10, 11]],
  [4, [15, 16]],
  [5, [48, 45]],
  [6, [15, 16]],
  [7, [15, 16]],
  [8, [2, 13]],
  [9, [2, 13]],
  [1, [2, 49, 4]],
  [1, [2, 13, 5]],
  [1, [2, 13, 6]],
  [1, [2, 13, 7]],
  [1, [2, 13]],
  [1, [2, 13]],
  [1, [2, 13]],
  [1, [2, 13]],
  [1, [2, 13, 8]],
  [1, [2, 13]],
  [2, [2, 13]],
];
</script>

<template>
  <!-- <div v-if="familyTree.length > 2"> -->
  <div id="main-content">
    <header>
      <!--page title, tagline and main graphic-->

      <br />
      <!--spacer-->

      <div id="hgroup">
        <!--main title group-->
        <h1>From Tree to Tree</h1>
        <h2>Genealogical Website<br />for the "Falkman Family"</h2>
      </div>
      <!--end main title group-->

      <!--DO NOT REMOVE!-->
      <div class="clear"></div>

      <br />
      <!--spacer-->

      <div id="headerimage"></div>
      <!--main page graphic or logo-->

      <div
        class="sectionline"
        style="float: right; margin: 0px 15px 0px 0px; width: 52%"
      ></div>
      <!--section divider-->
    </header>
    <!--end page header-->

    <!--for links: onclick triggers JS pop-up window. Maintain href links for those not using JavaScript-->

    <section class="intro" style="left: 0px; top: -20px; right: -100px; width: 1024px">
      <!--intro section-->
      <img src="@/assets/graphics/animation2.gif" alt="familygif" />
      <div class="topsection">
        <!-- <section
          class="topcontentBox3a wow fadeIn animated"
          data-wow-delay="0.2s"
          style="visibility: visible; animation-delay: 0.2s; animation-name: fadeIn"
        >
          <figure class="snip" style="width: 40%; float: left">
            <img src="@/assets/img/top1.jpg" alt="" />
            <figcaption>
              <p class="title1">Surnames</p>
            </figcaption>
          </figure>
        </section> -->
      </div>

      <article class="introarticle">
        <h3>This is a Website of the Falkman Family History</h3>
        <p class="dropcap">
          I started this adventure back in 1978. There were no online services at the
          time. All of the research was done by hand. I spent months and months searching
          through records and micro-fiche files for scraps of information. It took my wife
          and myself almost two (2) years just to find my great-grandfather's ship
          manifest. But that was just the start. Then came my great-grandmother's records,
          and after that, aunts, uncles and cousins. I hope you enjoy looking at the
          records and pictures as much as I did while putting this site together.
          <br />
          <br />
          This website was first published in 2010. The canvas didn't change much for many
          years but, now with the help of my family, I am updating the website, adding new
          templates and a lot of new information that has been discovered over the years.
          I want to thank all my family for the information and support that they have
          given.
          <p style="float: right; top: -20px; position: relative; right: 40px">Al F</p>
        </p>
      </article>
      <Animation />
      <aside class="panel">
        <h4 style="top: -20px">Page Links Here</h4>
        <div class="panelleft">
          <p class="p2" style="line-height: 200%" v-for="n in 5">
            <!-- <FamilyPage :index="n" />> -->
          </p>
        </div>
        <div class="panelright">
          <p class="p2" style="line-height: 200%" v-for="n in 5">
            <!-- <FamilyPage :index="n" />> -->
          </p>
        </div>
      </aside>

      <div class="clear"></div>
      <div class="sectionline"></div>
    </section>

    <div v-if="brothersData">
      <Tree
        :recordData="brothersData[0]"
        :infoTable="infoTable"
        :familyTree="familyTree"
        :familyTreeLocs="familyTreeLocs"
      />
    </div>
  </div>
  <p align="center">
    <GoBack />
  </p>
  <!-- <BackToTop /> -->
</template>

<style scoped>
@import "@/assets/css/familytree.css";
h4 {
  background-color: transparent;
}

aside.panel {
  top: 90px;
  right: 20px;
  height: 180px;
  width: 165px;
  text-align: center;
}
h2 {
  float: right;
}
#hgroup {
  width: 750px;
  left: 200px;
  float: none;
}
.p2 {
  margin: 0px;
}
.panelleft {
  left: 0px;
}
.panelright {
  right: 0px;
}
#main-content {
  position: absolute;
  width: 100%;
}
h1 {
  position: relative;
  margin: 0px 0px 0px 0px;
  font-family: Carolingia;
  font-size: 5em;
  color: #00b200;
  text-shadow: 2px 2px 10px rgba(0, 102, 0, 0.8);
  letter-spacing: 1px;
  line-height: 100%;
  background-color: inherit;
}
</style>
