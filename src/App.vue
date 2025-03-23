<script setup lang="ts">
import { ref } from 'vue';

const steps = [
  { key: "inhale", label: "Inhale" },
  { key: "hold1", label: "Hold" },
  { key: "exhale", label: "Exhale" },
  { key: "hold2", label: "Hold" },
];
const phase = ref();
const isRunning = ref(false)
const duration = 3
let breathIntervalId = 0
let counterIntervalId = 0
const counter = ref(0)

const handleStartPause = () => {
  isRunning.value = !isRunning.value
  if (isRunning.value) {
    phase.value = "inhale"
    doBreathe()
  } else {
    clearInterval(breathIntervalId)
    clearInterval(counterIntervalId)
    phase.value = ""
    counter.value = 0
  }
};

function doBreathe() {
  if (!isRunning) return;

  let currentStepIndex = steps.findIndex(step => step.key === phase.value);

  counter.value = 1
  counterIntervalId = setInterval(() => {
    counter.value++
    if (counter.value > duration) {
      counter.value = 1
    }
  }, 1000);

  breathIntervalId = setInterval(() => {
    currentStepIndex = (currentStepIndex + 1) % steps.length;
    phase.value = steps[currentStepIndex].key
  }, duration * 1000);
}
</script>

<template>
  <div class="container">
    <h1 class="title">Box Breathing</h1>
    <div class="wrapper">
      <div :class="[
        { ['inhale']: (phase === 'inhale' || phase === 'hold1') },
        { ['exhale']: (phase === 'exhale' || phase === 'hold2') },
        'circle'
      ]">
      </div>
      <div class="counter">{{ counter || "" }}</div>
    </div>
    <h2>{{steps.find(step => step.key === phase)?.label}}</h2>
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
  position: relative;
}

.circle {
  width: 100px;
  height: 100px;
  background: lightgray;
  border-radius: 50%;
  opacity: 0.6;
  box-shadow: 0px 0px 20px 5px rgba(0,0,0,0.2);
-webkit-box-shadow: 0px 0px 20px 5px rgba(0,0,0,0.2);
-moz-box-shadow: 0px 0px 20px 5px rgba(0,0,0,0.2);
}

.counter {
  font-size: 2rem;
  color: lightslategray;
  font-weight: bold;
  position: absolute;
  top: 50%;
  left: 50%;
  translate: -50% -50%;
  z-index: 1;
  opacity: 0.5;
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
