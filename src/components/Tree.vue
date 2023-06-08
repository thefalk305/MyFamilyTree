<script setup>
import { reactive, ref } from "vue";
import Branch from "./Branch.vue";
import ShowModal from "./ShowModal.vue";
import ImageContainers from "@/views/ImageContainers.vue";
import ImageContainer from "./ImageContainer.vue";
import FamilyPage from "@/views/FamilyPage.vue";

const props = defineProps({
  recordData: Object,
  infoTable: Array,
});
// var familyTree = ref([]);
var branchData = ref([]);
var branchLoc = ref([]);
// position each branch in the tree [top, left, width]
const familyTreeLocs = [
  [50, -350, 370], // mgroup0
  [196, -75, 370], // mgroup1
  [434, -580, 370], // mgroup2
  [434, 414, 370], // mgroup3
  [718, -1383, 470], // mgroup4
  [718, -460, 370], // mgroup5
  [718, 279, 370], // mgroup6
  [718, 1154, 470], // mgroup7
  [1002, -2000, 370], // mgroup8
  [1002, -1450, 370], // mgroup9
  [1002, -900, 370], // mgroup11
  [1002, -350, 370], // mgroup11
  [1002, 200, 370], // mgroup12
  [1002, 750, 370], // mgroup13
  [1002, 1300, 370], // mgroup14
  [1002, 1850, 370], // mgroup15
  [1286, -2635, 370], // mgroup16
  [1286, -2000, 370], // mgroup17
  [1356, -1272, 370], // mgroup18
  [1286, 1955, 370], // mgroup19
  [1286, 2485, 370], // mgroup20
  [1536, -3355, 370], // mgroup21
  [1536, -505, 370], // mgroup22
  [1806, -3726, 370], // mgroup23
  [1806, -3005, 370], // mgroup24
  [1806, -1185, 370], // mgroup25
  [1806, 600, 370], // mgroup26
  [2066, -3305, 370], // mgroup27
  [2066, -2605, 370], // mgroup28
  [2066, -1485, 370], // mgroup29
  [2066, -785, 370], // mgroup30
  [2066, 400, 370], // mgroup31
  [2326, -3005, 370], // mgroup32
  [2326, -2455, 370], // mgroup33
  [2326, -1785, 370], // mgroup34
  [2326, -1085, 370], // mgroup35
  [2326, -485, 370], // mgroup36
  [2326, 100, 370], // mgroup37
  [2586, -2085, 370], // mgroup42
  [2586, -1385, 370], // mgroup38
  [2586, 485, 370], // mgroup43
  [2846, -1085, 370], // mgroup39
  [3106, -1485, 370], // mgroup40
  [3366, -1785, 370], // mgroup41

];
// id's in database table of each family member
// determines who is in each branch
const familyTree = [
  [0, [4, 5, 6, 7, 8]],
  [1, [2, 13]],
  [2, [17, 39]],
  [3, [10, 11]],
  [4, [15, 16]],
  [5, [48, 45]],
  [6, [55, 56]],
  [7, [26, 28]],
  [8, [57, 58]],
  [9, [59, 60, 61]],
  [10, [68, 49, 4]],
  [11, [46, 69, 5]],
  [12, [2, 13, 6]],
  [13, [2, 13, 7]],
  [14, [2, 13]],
  [15, [29, 30]],
  [16, [62, 63, 99]],
  [17, [64, 65]],
  [18, [66, 67]],
  [19, [31, 32]],
  [20, [70, 71, 4]],
  [21, [73, 74]],
  [22, [72, 76]],
  [23, [100, 101]],
  [24, [102, 103]],
  [25, [75, 77]],
  [26, [78, 79]],
  [27, [104, 105]],
  [28, [108, 109]],
  [29, [82, 83]],
  [30, [85, 115]],
  [31, [80, 81]],
  [32, [110, 111]],
  [33, [112, 113]],
  [34, [84, 117]],
  [35, [86, 87]],
  [36, [98, 116]],
  [37, [94, 95]],
  [42, [114, 117]],
  [38, [88, 89]],
  [43, [96, 97]],
  [39, [90, 91]],
  [40, [92, 117]],
  [41, [93, 117]],
];

familyTree.forEach((value) => branchData.value.push(value));
familyTreeLocs.forEach((value) => branchLoc.value.push(value));

// these functions enable moving treewindow on screen
window.onload = function () {
  let draggableElem = document.getElementById("draggable-elem");
  let initialX = 0,
    initialY = 0;
  let moveElement = false;
  let stopMovement = false;
  let events = {
    mouse: {
      down: "mousedown",
      move: "mousemove",
      up: "mouseup",
      dblclick: "dblclick",
    },
    touch: {
      down: "touchstart",
      move: "touchmove",
      up: "touchend",
    },
  };

  let deviceType = "";

  const isTouchDevice = () => {
    try {
      //We try to create TouchEvent (it will fail for desktops and throw error)
      document.createEvent("touchEvent");
      deviceType = "touch";
      return true;
    } catch (e) {
      deviceType = "mouse";
      return false;
    }
  };

  isTouchDevice();
  // console.log(isTouchDevice());
  // Start (mouse down / touch start)
  draggableElem.addEventListener(events[deviceType].down, (e) => {
    e.preventDefault();
    // initial x and y points
    initialX = !isTouchDevice() ? e.clientX : e.touches[0].clientX;
    initialY = !isTouchDevice() ? e.clientY : e.touches[0].clientY;

    // start movement
    moveElement = true;
    console.log("mousedown");
  });

  draggableElem.addEventListener(events[deviceType].move, (e) => {
    if (moveElement) {
      e.preventDefault();
      let newX = !isTouchDevice() ? e.clientX : e.touches[0].clientX;
      let newY = !isTouchDevice() ? e.clientY : e.touches[0].clientY;
      draggableElem.style.top = draggableElem.offsetTop - (initialY - newY) + "px";
      draggableElem.style.left = draggableElem.offsetLeft - (initialX - newX) + "px";
      initialX = newX;
      initialY = newY;
    }
  });

  draggableElem.addEventListener(events[deviceType].dblclick, (e) => {
    if (true) {
      e.preventDefault();
      let newX = !isTouchDevice() ? e.clientX : e.touches[0].clientX;
      let newY = !isTouchDevice() ? e.clientY : e.touches[0].clientY;
      // draggableElem.style.top = draggableElem.offsetTop - (0 + newY) + "px"; 334
      // draggableElem.style.left = draggableElem.offsetLeft - (0 + newX) + "px"; 618
      draggableElem.style.top = 10 + newY + "px";
      draggableElem.style.left = -60 + newX + "px";
      initialX = newX;
      initialY = newY;

      console.log("dblClick");
    }
  });

  // mouse up / touch end

  draggableElem.addEventListener(
    events[deviceType].up,
    (stopMovement = (e) => {
      moveElement = false;
    })
  );

  draggableElem.addEventListener("mouseleave", stopMovement);
  draggableElem.addEventListener(events[deviceType].up, (e) => {
    moveElement = false;
  });
};
</script>

<template>
  <div id="treewindow">
    <img
      class="background"
      src="@/assets/graphics/treewindow.gif"
      alt=""
      height="2000"
      style="left: 0px"
    />

    <div id="draggable-elem" style="left: 565px; top: 470px">
      <!--this is the main tree container. All "mgroup" inline positioning below is based from the position of the treepot in the tree window-->
      <div id="treepot">
        <Branch
          v-for="(branch, index) in branchData"
          class="branch"
          :index="index"
          :recordData="recordData"
          :infoTable="infoTable"
          :branchData="branch"
          :branchLoc="branchLoc[index]"
        />
        <!--INFOBOX 00-->
        <figure class="boxzero">
          <h4 class="figs">How To Use This Tree:</h4>
          <p class="p2" style="text-align: justify">
            Grab and drag the white surface to navigate the tree. You can also
            double-click on a spot to center it in the window.<br />
            <br />
            Use the lightbox in the infopages for quick viewing, or right-click each photo
            link and open the full-sized image in a new tab or window&mdash;perfect for
            reading the documents, or if you wish to download anything.
          </p>
        </figure>

        <!--INFOBOX 01-->
        <figure class="boxone" style="left: -620px">
          <h4>&#8656;&nbsp;&nbsp;This Way To:</h4>
          <p class="p2" style="line-height: 200%" v-for="n in 5">
            <!-- <FamilyPage :index="n" /> -->
          </p>
        </figure>

        <!--INFOBOX 02-->
        <figure class="boxtwo" style="left: 600px">
          <h4 class="figs">This Way To:&nbsp;&nbsp;&#8658;</h4>
          <p class="p2" style="line-height: 200%" v-for="n in 5">
            <!-- <FamilyPage :index="n" /> -->
          </p>
        </figure>

        <!--INFOBOX 03-->
        <figure class="boxthree">
          <p class="p2" style="text-align: justify">New branches growing soon!</p>
        </figure>

        <!--INFOBOX 04-->
        <figure class="boxfour">
          <p class="p2" style="text-align: justify">New branches growing soon!</p>
        </figure>
      </div>
      <!--end treepot-->
    </div>
    <!--end treepot container-->
  </div>
  <!--end treewindow-->
</template>

<style scoped>
h4 {
  background-color: transparent;
}
/*
.mgroup {
  left: 300px;
  top: 20px;
  position: absolute;
  width: 370px;
  height: 140px;
  border-radius: 12px 24px 24px 24px;
  border-top: thin #006600 solid;
  border-left: thin #006600 solid;
  border-right: thin #006600 solid;
  z-index: 1;
}
*/
#tree {
  position: relative;
}
#treewindow {
  position: relative;
  margin: 0px auto 40px auto;
  display: block;
  width: 98%;
  height: 700px;
  background-color: white;
  background-image: url(../assets/graphics/treewindow.png);
  background-size: 100%;
  background-repeat: no-repeat;
  cursor: url(../assets/graphics/openhand.cur), pointer;
  overflow: visible;
  z-index: 99;
}
#image-container {
  width: 214px;
  height: 400px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  box-sizing: content-box;
}
</style>
