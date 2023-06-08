<template>
  <p class="go-back" align="center">
    <button @click="$router.back()">go Back!</button>
  </p>
</template>

<style scoped>
.go-back {
  left: 0;
  position: absolute;
  bottom: 10px;
  right: 0;
}
</style>
