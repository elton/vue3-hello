<script setup>
import { ref, onMounted } from 'vue';

// Section 9: Lifecycle and Template refs
const p = ref(null);
onMounted(() => {
  p.value.textContent = 'Hello, world!';
});
</script>

<template>
  <div>
    <p ref="p">hello</p>
  </div>
</template>
