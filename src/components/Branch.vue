<script setup>
import { reactive, ref, watchEffect } from "vue";
import ImageCont from "./ImageCont.vue";

const props = defineProps({
  recordData: Object,
  infoTable: Array,
  index: Number,
  branchData: Array,
  branchLoc: Array,
});

var coupleData = ref([]);
var branchIds = ref([]);
var branchGroup = ref();
var posX = ref();
var posY = ref();
var wide = ref();
// twigData determines position of each 'twig' (interconnecting lines) on family tree
const twigData = [
  [[[""]], [[""]], [["ibtopline"]]],
  [ // mgroup1
    [["leftwig"], ["left:-319px; width:319px; height:162px"]],
    [["rightwig"], ["left:355px; width:319px; height:162px"]],
    [["stline"]],
  ],
  [ // mgroup2
    [["leftwig"], ["left:-450px; width:450px; height:206px"]],
    [["rightwig"], ["left:365px; width:5px; height:206px"]],
    [[""]],
  ],
  [ // mgroup3
    [["leftwig"], ["left:0px; width:5px; height:206px"]],
    [["rightwig"], ["left:400px; width:500px; height:206px"]],
    [[""]],
  ],
  [ // mgroup4
    [["leftwig"], ["left:-450px; width:450px; height:208px"]],
    [["leftwig"], ["top:208px; left:200px; width:245px; height:75px"]],
    [["upcurve1"]],
  ],
  [ // mgroup5
    [["leftwig"], ["left:-250px; width:250px; height:208px"]],
    [["rightwig"], ["left:360px; width:5px; height:208px"]],
    [[""]],
  ],
  [ // mgroup6
    [["leftwig"], ["left:0px; width:5px; height:208px"]],
    [["rightwig"], ["left:355px; width:300px; height:208px"]],
    [[""]],
  ],
  [ // mgroup7
    [["rightwig"], ["left:25px; top: 208px; width:219px; height:75px"]],
    [["rightwig"], ["left:450px; width:400px; height:208px"]],
    [["upcurve2"]],
  ],
  [ // mgroup8
    [["leftwig"], ["left:-450px; width:450px; height:208px"]],
    [["leftwig"], ["top:208px; left:190px; width: 156px; height:75px"]],
    [["upcurve1"]],
  ],
  [ // mgroup9
    [["leftwig"], ["left:369px; width:5px; height:277px"]],
    [["leftwig"], ["top:230px; left:22px; width:150px; height:1px"]],
    [["upcurve2"], ["top:130px"]],
  ],
  [ // mgroup10
    [["rightwig"], ["left:25px; top: 230px; width:200px; height:1px"]],
    [["upcurve2"], ["top:130px"]],
    [[""]],
  ],
  [ // mgroup11
    [["rightwig"], ["left:25px; top: 230px; width:200px; height:1px"]],
    [["upcurve2"], ["top:130px"]],
    [[""]],
  ],
  [ // mgroup12
    [["rightwig"], ["left:25px; top: 230px; width:200px; height:1px"]],
    [["upcurve2"], ["top:130px"]],
    [[""]],
  ],
  [ // mgroup13
    [["rightwig"], ["left:25px; top: 230px; width:200px; height:1px"]],
    [["upcurve2"], ["top:130px"]],
    [[""]],
  ],
  [ // mgroup14
    [[""], [""]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup15
    [["rightwig"], ["left:25px; top: 208px; width:215px; height:75px"]],
    [["rightwig"], ["left:415px; width:400px; height:208px"]],
    [["upcurve2"]],
  ],
  [ // mgroup16
    [["leftwig"], ["left:-450px; width:450px; height:174px"]],
    [["leftwig"], ["top:230px; left:205px; width:150px"]],
    [["upcurve1"], ["top:130px"]],
  ],
  [ // mgroup17
    [[""], [""]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup18
    [["rightwig"], ["left:355px; width:556px; height:104px"]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup19
    [[""], [""]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup20
    [["rightwig"], ["left:25px; top: 230px; width:200px; height:1px"]],
    [["upcurve2"], ["top:130px"]],
    [[""]],
  ],
  [ // mgroup21
    [["leftwig"], ["left:-190px; width:200px; height:194px"]],
    [["rightwig"], ["left:355px; width:156px; height:194px"]],
    [[""], [""]],
  ],
  [ // mgroup22
    [["leftwig"], ["left:-590px; width:600px; height:194px"]],
    [["rightwig"], ["left:355px; width:856px; height:194px"]],
    [[""], [""]],
  ],
  [ // mgroup23
    [[""], [""]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup24
    [["leftwig"], ["left:-190px; width:200px; height:184px"]],
    [["rightwig"], ["left:355px; width:156px; height:184px"]],
    [[""], [""]],
  ],
  [ // mgroup25
    [["leftwig"], ["left:-120px; width:80px; height:184px"]],
    [["rightwig"], ["left:355px; width:156px; height:184px"]],
    [[""], [""]],
  ],
  [ // mgroup26
    [["leftwig"], ["left:-90px; width:100px; height:184px"]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup27
    [[""], [""]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup28
    [["leftwig"], ["left:-120px; width:80px; height:184px"]],
    [["rightwig"], ["left:355px; width:100px; height:184px"]],
    [[""], [""]],
  ],
  [ // mgroup29
    [[""], [""]],
    [[""], [""]],
    [["leftwig"], ["left:-190px; width:200px; height:184px"]],
  ],
  [ // mgroup30
    [["leftwig"], ["left:-190px; width:200px; height:184px"]],
    [["rightwig"], ["left:355px; width:156px; height:184px"]],
    [[""], [""]],
  ],
  [ // mgroup31
    [["leftwig"], ["left:-190px; width:200px; height:184px"]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup32
    [[""], [""]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup33
    [[""], [""]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup34
    [["leftwig"], ["left:-190px; width:200px; height:184px"]],
    [[""], [""]],
    [[""], [""]],
  ],
   [ // mgroup35
    [["leftwig"], ["left:-190px; width:200px; height:184px"]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup36
    [[""], [""]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup37
    [["rightwig"], ["left:355px; width:156px; height:184px"]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup42
    [[""], [""]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup38
    [["rightwig"], ["left:355px; width:156px; height:184px"]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup43
    [[""], [""]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup39
    [["leftwig"], ["left:-190px; width:200px; height:184px"]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup40
    [["leftwig"], ["left:-190px; width:200px; height:184px"]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup41
    [[""], [""]],
    [[""], [""]],
    [[""], [""]],
  ],
  [ // mgroup44
    [[""], [""]],
    [[""], [""]],
    [[""], [""]],
  ],
];
var sty1 = ref("");
var sty2 = ref("");
var sty3 = ref("");
var class1 = ref("");
var class2 = ref("");
var class3 = ref("");

branchIds.value = props.branchData[1];
branchGroup.value = props.branchData[0];

branchIds.value.forEach((item, index) => {
  // console.log(item);
  coupleData.value[index] = props.infoTable[item - 1];
});

// coupleData.value[0] = props.infoTable[branchIds.value[0] - 1];
// coupleData.value[1] = props.infoTable[branchIds.value[1] - 1];
posY = props.branchLoc[0] + "px";
posX = props.branchLoc[1] + "px";
wide = props.branchLoc[2] + "px";

class1.value = twigData[props.index][0][0];
class2.value = twigData[props.index][1][0];
class3.value = twigData[props.index][2][0];
sty1.value = twigData[props.index][0][1];
sty2.value = twigData[props.index][1][1];
sty3.value = twigData[props.index][2][1];
</script>

<template>
  <div v-if="index === 0" class="topmgroup">
    <div
      v-for="(item, id) in coupleData"
      :key="item.id"
      :style="{ top: '50px', left: id * 200 + 'px', position: 'absolute' }"
    >
      <ImageCont :recordData="item" :id="id + 2" />
    </div>
    <div id="ibtopline" :style="{ height: '2px', left: '60px' }"></div>
  </div>
  <div v-else :id="'mgroup' + index" class="mgroup" :style="{ top: posY, left: posX, width: wide }">
  <p style="top: -12px; position: absolute" >mgroup{{index}}</p>
    <div v-for="(item, id) in coupleData" :key="item.id">
      <ImageCont
        v-if="id < 2"
        :class="id ? 'female' : 'male'"
        :recordData="item"
        :id="id"
      />
      <ImageCont v-else class="male-female" style="top: 174px" :recordData="item" />
    </div>
    <!-- class/style for twigs -->
    <div :class="[class1]" :style="[sty1]"></div>
    <div :class="[class2]" :style="[sty2]"></div>
    <div :class="[class3]" :style="[sty3]"></div>
  </div>
</template>

<style scoped>
#ibtopline {
  position: absolute;
  top: 55px;
  left: 00px;
  height: 1px;
  width: 800px;
  background-color: #006600;
  box-shadow: 2px 2px 7px rgba(0, 102, 0, 0.6);
  z-index: 0;
}
#ibtopline {
  position: absolute;
  top: 110px;
  left: -300px;
  height: 2px;
  width: 800px;
  background-color: #006600;
  box-shadow: 2px 2px 7px rgba(0, 102, 0, 0.6);
  z-index: 0;
}

.topmgroup {
  position: absolute;
  top: -40px;
  left: -350px;
  width: 920px;
  height: 170px;
}
#image-container {
  width: 214px;
  height: 400px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  box-sizing: content-box;
  border-bottom: none;
}
.mgroup {
  position: absolute;
  width: 370px;
  height: 140px;
  border-radius: 12px 24px 24px 24px;
  border-top: thin #006600 solid;
  border-left: thin #006600 solid;
  border-right: thin #006600 solid;
  border-bottom: none;

  z-index: 1;
}

.male {
  left: -50px;
  bottom: 0px;
}
.female {
  right: -50px;
  bottom: 0px;
}
</style>
