<script setup lang="ts">
</script>

<template>
  <div>
    <h1 id="title">I am Kalm</h1>
    <div id="breath"></div>
  </div>
</template>

<style scoped>
#title {
  text-align: center;
}

#breath {
  width: 300px;
  height: 300px;
  background: aqua;
  border-radius: 50%;
  animation-duration: 3s;
  animation-name: breath-in-out;
  animation-iteration-count: infinite;
  animation-direction: alternate;
  animation-timing-function: ease-in-out;
}

@keyframes breath-in-out {
  from {
    scale: 0%;
  }

  to {
    scale: 100%;
  }
}
</style>
