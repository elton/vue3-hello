<script setup>
const props = defineProps({
  num: String,
  title: String,
});
</script>
<template>
  <div
    class="w-3/4 rounded-lg border border-slate-100 bg-teal-50 p-4 text-center text-neutral-600"
  >
    <h2 class="mb-1 text-left text-lg font-semibold text-teal-800">
      Step {{ num }}: <span class="text-base italic">{{ title }}</span>
    </h2>
    <slot />
  </div>
</template>
