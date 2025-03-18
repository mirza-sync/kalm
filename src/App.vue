<script setup lang="ts">
import { ref } from 'vue';

const steps = ["inhale", "hold1", "exhale", "hold2"];
const phase = ref();
const isRunning = ref(false)
const duration = 3
let intervalId = 0

const handleStartPause = () => {
  isRunning.value = !isRunning.value
  if (isRunning.value) {
    phase.value = "inhale"
    doBreathe()
  } else {
    clearInterval(intervalId)
    phase.value = ""
  }
};

function doBreathe() {
  if (!isRunning) return;

  let currentStepIndex = steps.indexOf(phase.value);

  intervalId = setInterval(() => {
    currentStepIndex = (currentStepIndex + 1) % steps.length;
    phase.value = steps[currentStepIndex]
  }, duration * 1000);
}
</script>

<template>
  <div class="container">
    <h1 class="title">I nid Kalm</h1>
    <div class="wrapper">
      <div :class="[
        { ['inhale']: (phase === 'inhale' || phase === 'hold1') },
        { ['exhale']: (phase === 'exhale' || phase === 'hold2') },
        'circle'
      ]">
      </div>
    </div>
    <div>
      {{ phase }}
    </div>
    <button type="button" @click="handleStartPause()">{{ !isRunning ? 'Start' : 'Stop' }}</button>
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
}

.inhale {
  animation-name: inhale-or-hold1;
  animation-duration: 3s;
  animation-iteration-count: 1;
  animation-timing-function: ease-in-out;
  animation-fill-mode: forwards;
}

.exhale {
  animation-name: exhale-or-hold2;
  animation-duration: 3s;
  animation-iteration-count: 1;
  animation-timing-function: ease-in-out;
  animation-fill-mode: forwards;
}

@keyframes inhale-or-hold1 {
  from {
    transform: scale(1);
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
    transform: scale(1);
  }
}
</style>
