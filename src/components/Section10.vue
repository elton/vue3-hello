<script setup>
import { ref, watch } from 'vue';

// Section 10: Watchers
// watch() can directly watch a ref, and the callback gets fired whenever count's value changes.
const todoID = ref(1);
const todoData = ref(null);

const fetchData = async () => {
  todoData.value = null;
  const res = await fetch(
    `https://jsonplaceholder.typicode.com/todos/${todoID.value}`
  );
  todoData.value = await res.json();
};

fetchData();
watch(todoID, fetchData);
</script>
<template>
  <div>
    <p>Todo ID:{{ todoID }}</p>
    <button @click="todoID++" class="btn-primary mt-2">Fetch next todo</button>
    <p v-if="!todoData">Loading...</p>
    <pre
      v-else
      class="mt-4 border-t border-neutral-300 pt-2 font-mono text-sm text-neutral-700"
      >{{ todoData }}</pre
    >
  </div>
</template>
