<script setup>
import { ref } from 'vue';

const count = ref(0);
const increment = () => count.value++;
</script>
<template>
  <!-- Event Listeners. it's a shorthand syntax of v-on -->
  <button @click="increment" class="btn-primary">count is: {{ count }}</button>
</template>
