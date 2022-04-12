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

const titleClass = ref('title');

const count = ref(0);
const increment = () => count.value++;

const text = ref('');
</script>

<template>
  <div class="m-4 space-y-2">
    <h1 class="text-3xl font-bold underline">{{ message }}</h1>
    <!-- Notice how we did not need to use .value when accessing the message ref in templates: it is automatically unwrapped for more succinct usage. -->
    <p>count is:{{ counter.count }}</p>
    <!-- The content inside the mustaches is not limited to just identifiers or paths - we can use any valid JavaScript expression: -->
    <div>
      {{ message.split('').reverse().join('') }}
    </div>
    <!-- Attribute Bindings, it's a shorthand syntax of v-bind -->
    <p :class="titleClass">Make me red</p>
    <!-- Event Listeners. it's a shorthand syntax of v-on -->
    <button @click="increment" class="rounded bg-sky-600 px-5 text-white">
      count is: {{ count }}
    </button>
    <div class="flex space-x-2">
      <!-- v-model automatically syncs the <input>'s value with the bound state -->
      <input
        v-model="text"
        placeholder="Type here"
        type="text"
        class="rounded border p-1 text-sm"
      />
      <p>{{ text.toUpperCase() }}</p>
    </div>
  </div>
</template>

<style>
.title {
  color: red;
}
</style>
