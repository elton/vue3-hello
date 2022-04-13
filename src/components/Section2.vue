<script setup>
import { reactive, ref } from 'vue';
// reactive() only works on objects (including arrays and built-in types like Map and Set).
// State that can trigger updates when changed are considered reactive.
// When the state changes, the HTML updates automatically.
const counter = reactive({
  count: 1,
});

// console.log(counter.count);
// counter.count++;

// ref(), on the other hand, can take any value type and create an object that exposes the inner value under a .value property
const message = ref('Hello, world!');

// console.log(message.value);
// message.value = 'changed';
</script>
<template>
  <h1 class="text-3xl font-bold underline">{{ message }}</h1>
  <!-- Notice how we did not need to use .value when accessing the message ref in templates: it is automatically unwrapped for more succinct usage. -->
  <p>count is:{{ counter.count }}</p>
  <!-- The content inside the mustaches is not limited to just identifiers or paths - we can use any valid JavaScript expression: -->
  <p>
    {{ message.split('').reverse().join('') }}
  </p>
</template>
