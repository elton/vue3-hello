<script setup>
import { ref } from 'vue';
const titleClass = ref('title');
</script>

<template>
  <!-- Attribute Bindings, it's a shorthand syntax of v-bind -->
  <p :class="titleClass">Make me red</p>
</template>

<style>
.title {
  color: red;
}
</style>
