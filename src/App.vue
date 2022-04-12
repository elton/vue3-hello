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

const awesome = ref(true);
const toggle = () => {
  awesome.value = !awesome.value;
};

let id = 0;
const newTodo = ref('');
const todos = ref([
  { id: id++, text: 'Learn Vue', done: false },
  { id: id++, text: 'Learn React', done: false },
  { id: id++, text: 'Learn Nuxt', done: false },
]);

const addTodo = () => {
  todos.value.push({
    id: id++,
    text: newTodo.value,
    done: false,
  });
  newTodo.value = '';
};

const removeTodo = (todo) =>
  (todos.value = todos.value.filter((t) => t.id !== todo.id));
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

    <div class="w-1/4 text-center">
      <p v-if="awesome">Vue is awesome!</p>
      <p v-else>oh, no. 🤣</p>
      <button @click="toggle" class="w-24 rounded bg-slate-600 px-1 text-white">
        toggle
      </button>
    </div>

    <div>
      <input
        type="text"
        class="rounded border border-neutral-400 p-1 text-sm"
        v-model="newTodo"
        @keyup.enter="addTodo"
        placeholder="Type new todo"
      />
      <button
        @click="addTodo"
        class="ml-2 rounded bg-neutral-600 px-2 text-white"
      >
        Add todo
      </button>
      <ul>
        <li
          v-for="todo in todos"
          :key="todo.id"
          class="mt-2 flex items-center text-sm text-neutral-600"
        >
          <p>{{ todo.text }}</p>
          <button
            @click="removeTodo(todo)"
            class="ml-2 rounded border bg-amber-800 px-2 text-sm text-white"
          >
            x
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<style>
.title {
  color: red;
}
</style>
