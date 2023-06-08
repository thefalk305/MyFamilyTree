<script setup>
import { reactive, ref } from "vue";
import ShowModal from "./ShowModal.vue";
import bldRels from "@/assets/js/buildRelatives.js";

const props = defineProps({
  recordData: Object,
  infoTable: Array,
});
var showRelatives = ref(false);

var tblArray = ref([]);
var tblKeys = Object.keys(props.recordData);
var tblValues = props.recordData.valueOf();
// debugger;
tblArray = bldRels(tblKeys, props.infoTable, props.recordData);

// tblArray holds ids and names of each relative
// var i = 0;
// for (i = 0; i < tblKeys.length; i++) {
//   if (tblKeys[i] == "spouse" && !(spouse === "")) {
//     tblArray.value.push({ id: 0, name: "Spouse:" });
//     tblArray.value.push({
//       ...props.infoTable[findId(spouse) - 1],
//       id: findId(spouse),
//       name: spouse,
//     });
//   }

//   if (tblKeys[i] == "father") {
//     tblArray.value.push({ id: 0, name: "Parents:" });
//     tblArray.value.push({
//       ...props.infoTable[findId(father) - 1],
//       id: findId(father),
//       name: father,
//     });
//     tblArray.value.push({
//       ...props.infoTable[findId(mother) - 1],
//       id: findId(mother),
//       name: mother,
//     });
//   }
//   if (tblKeys[i] === "sib1" && !(sib1 === "")) {
//     tblArray.value.push({ id: 0, name: "Siblings:" });
//     tblArray.value.push({
//       ...props.infoTable[findId(sib1) - 1],
//       id: findId(sib1),
//       name: sib1,
//     });
//     tblArray.value.push({
//       ...props.infoTable[findId(sib2) - 1],
//       id: findId(sib2),
//       name: sib2,
//     });
//     tblArray.value.push({
//       ...props.infoTable[findId(sib3) - 1],
//       id: findId(sib3),
//       name: sib3,
//     });
//     tblArray.value.push({
//       ...props.infoTable[findId(sib4) - 1],
//       id: findId(sib4),
//       name: sib4,
//     });
//     tblArray.value.push({
//       ...props.infoTable[findId(sib5) - 1],
//       id: findId(sib5),
//       name: sib5,
//     });
//     tblArray.value.push({
//       ...props.infoTable[findId(sib6) - 1],
//       id: findId(sib6),
//       name: sib6,
//     });
//   }
//   if (tblKeys[i] == "child1" && !(child1 === "")) {
//     tblArray.value.push({ id: 0, name: "Children:" });
//     tblArray.value.push({
//       ...props.infoTable[findId(child1) - 1],
//       id: findId(child1),
//       name: child1,
//     });
//     tblArray.value.push({
//       ...props.infoTable[findId(child2) - 1],
//       id: findId(child2),
//       name: child2,
//     });
//     tblArray.value.push({
//       ...props.infoTable[findId(child3) - 1],
//       id: findId(child3),
//       name: child3,
//     });
//     tblArray.value.push({
//       ...props.infoTable[findId(child4) - 1],
//       id: findId(child4),
//       name: child4,
//     });
//     tblArray.value.push({
//       ...props.infoTable[findId(child5) - 1],
//       id: findId(child5),
//       name: child5,
//     });
//     tblArray.value.push({
//       ...props.infoTable[findId(child6) - 1],
//       id: findId(child6),
//       name: child6,
//     });
//   }
// }
// // filter out blank fields
// tblArray = tblArray.value.filter((item) => {
//   return item.name != "";
// });
// // find correct id for each relative
// function findId(name) {
//   for (let i = 0; i < props.infoTable.length; i++) {
//     if (name == props.infoTable[i].name) {
//       return props.infoTable[i].id;
//     }
//   }
// }
// // filter out relatives without database records
// for (i = 0; i < tblArray.length; i++) {
//   if (tblArray[i].id === undefined) {
//     tblArray[i].id = 1; // use dummy id
//   }
// }
</script>

<template>
  <div>
    <ShowModal :recordData="recordData" />
    <!-- <p>&nbsp;</p> -->
    <div id="relatives">
      <button
        class="clickMe"
        type="input"
        style="position: relative; width: 196px"
        @click="showRelatives = !showRelatives"
      >
        {{ showRelatives ? "Hide Relatives" : "Show Relatives" }}
      </button>
      <div v-if="showRelatives">
        <table v-for="record in tblArray" v-bind:key="record.id">
          <!-- test whether heading or relative -->
          <div v-if="record.id == 0">
            <td>
              <h2>{{ record.name }}</h2>
            </td>
          </div>
          <div v-else>
            <td>
              <ShowModal :recordData="record" />
            </td>
          </div>
        </table>
      </div>
    </div>
  </div>
</template>

<style>
#relatives {
  position: absolute;
  display: flex;
  flex-direction: column;
}
.clickMe {
  border: none;
}
h2 {
  width: 214px;
  text-align: center;
}

h2 {
  width: 250px;
  font-style: italic;
  left: -50px;
  text-align: left;
}
</style>
