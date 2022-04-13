<script setup>
import { ref } from 'vue';
import ChildComp from './components/ChildComp.vue';
import Section2 from './components/Section2.vue';
import Section3 from './components/Section3.vue';
import Section4 from './components/Section4.vue';
import Section5 from './components/Section5.vue';
import Section6 from './components/Section6.vue';
import Section7 from './components/Section7.vue';
import Section9 from './components/Section9.vue';
import Section10 from './components/Section10.vue';
import Section from './components/Section.vue';

const greeting = ref('Hello from parent');
const childMsg = ref('No child msg yet');
const sections = ref([
  { num: '02', title: 'Declarative Rendering' },
  { num: '03', title: 'Attribute Bindings' },
  { num: '04', title: 'Event Listeners' },
  { num: '05', title: 'Form Bindings' },
  { num: '06', title: 'Conditional Rendering' },
  { num: '07-08', title: 'List Rendering & Computed Property' },
  { num: '09', title: 'Lifecycle and Template Refs' },
  { num: '10', title: 'Watchers' },
  { num: '11-14', title: 'Components, Props, Emits and slot' },
]);
</script>

<template>
  <h1 class="m-4 text-center text-3xl font-semibold text-emerald-800">
    {{ 'vue3 exercises'.toUpperCase() }}
  </h1>
  <p class="m-4 text-center text-neutral-600">
    Refer to
    <a
      href="https://staging-cn.vuejs.org/tutorial"
      class="text-sky-600 underline"
      >vue3 official tutorial</a
    >
  </p>
  <div class="m-4 flex flex-col items-center space-y-2">
    <Section
      :key="sections[0].num"
      :num="sections[0].num"
      :title="sections[0].title"
      ><Section2
    /></Section>
    <Section
      :key="sections[1].num"
      :num="sections[1].num"
      :title="sections[1].title"
      ><Section3
    /></Section>
    <Section
      :key="sections[2].num"
      :num="sections[2].num"
      :title="sections[2].title"
      ><Section4
    /></Section>
    <Section
      :key="sections[3].num"
      :num="sections[3].num"
      :title="sections[3].title"
      ><Section5
    /></Section>
    <Section
      :key="sections[4].num"
      :num="sections[4].num"
      :title="sections[4].title"
      ><Section6
    /></Section>
    <Section
      :key="sections[5].num"
      :num="sections[5].num"
      :title="sections[5].title"
      ><Section7
    /></Section>
    <Section
      :key="sections[6].num"
      :num="sections[6].num"
      :title="sections[6].title"
      ><Section9
    /></Section>
    <Section
      :key="sections[7].num"
      :num="sections[7].num"
      :title="sections[7].title"
      ><Section10
    /></Section>
    <Section
      :key="sections[8].num"
      :num="sections[8].num"
      :title="sections[8].title"
      ><ChildComp :msg="greeting" @response="(msg) => (childMsg = msg)">
        This is some slot content.
      </ChildComp>
      <p>{{ childMsg }}</p></Section
    >
  </div>
</template>
