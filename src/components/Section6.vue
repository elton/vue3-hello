<script setup>
import { ref } from 'vue';

const awesome = ref(true);
const toggle = () => (awesome.value = !awesome.value);
</script>
<template>
  <div>
    <p v-if="awesome">Vue is awesome!</p>
    <p v-else>oh, no. 🤣</p>
    <button @click="toggle" class="btn-primary mt-2">toggle</button>
  </div>
</template>
