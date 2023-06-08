<script setup>
import InfoTable from "@/views/InfoTable.vue";
import ImageContainers from "@/views/ImageContainers.vue";
import DaBoys from "@/views/DaBoys.vue";
import About from "@/views/About.vue";
import { ref, watch } from "vue";
const clocktext = ref("");

var tday = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
var tmonth = [
  "January",
  "February",
  "March",
  "April",
  "May",
  "June",
  "July",
  "August",
  "September",
  "October",
  "November",
  "December",
];

function GetClock() {
  var d = new Date();
  var nday = d.getDay(),
    nmonth = d.getMonth(),
    ndate = d.getDate();
  var nhour = d.getHours(),
    nmin = d.getMinutes(),
    nsec = d.getSeconds();
  if (nmin <= 9) nmin = "0" + nmin;
  if (nsec <= 9) nsec = "0" + nsec;

  clocktext.value =
    "" +
    tday[nday] +
    ", " +
    tmonth[nmonth] +
    " " +
    ndate +
    " " +
    nhour +
    ":" +
    nmin +
    ":" +
    nsec +
    "";
}

// GetClock();
var myInterval = setInterval(GetClock, 1000);
</script>

<template>
  <div id="nav" class="falkmans-web">
    <AppLink to="FamilyTree">Falkman<br />Family<br />Tree</AppLink>
    <!-- <AppLink to="http://localhost/new_falkmansweb/index.php"
      >Falkman<br />Family<br />Tree</AppLink
    > -->
    <AppLink to="FamilyHistory">Falkman<br />Family<br />History</AppLink>
    <AppLink to="http://falkman.com">Falkman<br />Family<br />History</AppLink>
    <AppLink to="DaBoys">Da' Boys</AppLink>
    <!-- <AppLink id="login" to="Login">Login</AppLink> -->
    <!-- <AppLink to="Test">Test</AppLink> -->
    <AppLink to="PhotoPages">Photo<br />Pages</AppLink>
    <AppLink :to="{ name: 'protected' }">Dashboard</AppLink>
    <AppLink to="InfoTable">Infotable</AppLink>
    <!-- <AppLink to="About">About</AppLink> -->
    <div id="clock">
      <div class="date">{{ clocktext }}</div>
    </div>
  </div>
</template>

<style scoped>
#nav.falkmans-web {
  color: #00ff80;
  border-bottom: 2px solid #00ff80;
}
.date {
  color: burlywood;
}
</style>
