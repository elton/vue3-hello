<script setup>
import { ref, computed } from 'vue';
import { TrashIcon } from '@heroicons/vue/outline';

let id = 0;
const newTodo = ref('');
const hideCompleted = ref(false);
const todos = ref([
  { id: id++, text: 'Learn Vue', done: false },
  { id: id++, text: 'Learn React', done: true },
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
// A computed property tracks other reactive state used in its computation as dependencies. It caches the result and automatically updates it when its dependencies change.
const filteredTodos = computed(() => {
  return hideCompleted.value ? todos.value.filter((t) => !t.done) : todos.value;
});
</script>

<template>
  <div class="flex flex-col items-center">
    <div>
      <input
        type="text"
        class="input"
        v-model="newTodo"
        @keyup.enter="addTodo"
        placeholder="Type new todo"
      />
      <button @click="addTodo" class="btn-primary ml-2">Add todo</button>
    </div>

    <ul>
      <li
        v-for="todo in filteredTodos"
        :key="todo.id"
        class="mt-2 flex items-center text-sm text-neutral-600"
      >
        <input
          type="checkbox"
          @click="todo.done = !todo.done"
          v-model="todo.done"
          class="mr-2"
        />
        <p
          class="text-sm text-neutral-700"
          :class="{ 'text-neutral-500 line-through': todo.done }"
        >
          {{ todo.text }}
        </p>
        <button @click="removeTodo(todo)">
          <TrashIcon class="ml-2 h-5 w-5" />
        </button>
      </li>
    </ul>
    <button @click="hideCompleted = !hideCompleted" class="btn-primary mt-2">
      {{ hideCompleted ? 'show all' : 'hide completed' }}
    </button>
  </div>
</template>
