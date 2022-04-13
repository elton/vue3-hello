<script setup>
// defineProps() is a compile-time macro and doesn't need to be imported.
// Once declared, the msg prop can be used in the child component's template.
const props = defineProps({
  msg: String,
});

// declare emitted events
const emit = defineEmits(['response']);

// emit with argument
// The first argument to emit() is the event name
// Any additional arguments are passed on to the event listener.
emit('response', 'Hello from child.');
</script>
<template>
  <div>{{ msg || 'No props pass yet' }}</div>
  <!-- Content inside the <slot> outlet will be treated as "fallback" content: it will be displayed if the parent did not pass down any slot content -->
  <slot />
</template>
