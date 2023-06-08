<script>
import GoBack from "../components/GoBack.vue";
import BackToTop from "@/components/BackToTop.vue";
import MiniNav from "@/components/MiniNav.vue";

export default {
	components: {
		GoBack,
		BackToTop,
		MiniNav,
	},
};
</script>

<template>
	<div id="chicago">
  <MiniNav />
<h1 align="center">Chicago, Illinois</h1>
<p>The Falkman's finally settle in Chicago. Here is were they set down their 
roots. With many generations born and living in and around the Chicago area. 
(More to follow)</p>
    <p align="center">
      <GoBack />
    </p>
  </div>
  <BackToTop />
</template>
