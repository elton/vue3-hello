<script setup>
import { ref } from 'vue';

const text = ref('');
</script>
<template>
  <div class="flex justify-center space-x-2">
    <!-- v-model automatically syncs the <input>'s value with the bound state -->
    <input v-model="text" placeholder="Type here" type="text" class="input" />
    <p>{{ text.toUpperCase() }}</p>
  </div>
</template>
