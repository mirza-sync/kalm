<script setup lang="ts">
function doBreathe() {
  const circle = document.getElementsByClassName("circle")[0];
  circle?.classList.toggle("breathe-animation");
}
</script>

<template>
  <div class="container">
    <h1 class="title">I nid Kalm</h1>
    <div class="wrapper">
      <div class="circle"></div>
    </div>
    <button type="button" @click="doBreathe()">Start</button>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

.title {
  text-align: center;
  margin-block: 0;
}

.wrapper {
  width: 50vw;
  height: 50vh;
  display: grid;
  place-items: center;
}

.circle {
  width: 100px;
  height: 100px;
  background: aqua;
  border-radius: 50%;
  transform: scale(0);
}

.breathe-animation {
  animation-name: inhale-or-hold1;
  animation-duration: 3s;
  animation-iteration-count: 1;
  animation-timing-function: ease-in-out;
}



@keyframes inhale-or-hold1 {
  from {
    transform: scale(0);
  }

  to {
    transform: scale(2);
  }
}

@keyframes exhale-or-hold2 {
  from {
    transform: scale(2);
  }

  to {
    transform: scale(0);
  }
}
</style>
