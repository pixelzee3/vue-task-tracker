<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  tasks: {
    type: Array,
    default: () => [],
  },
});
</script>
<template>
  <div class="px-8">
    <div
      v-for="task in props.tasks"
      :key="task.id"
      class="mt-4 flex justify-between rounded-lg px-2 py-4 first:mt-0"
      :class="{
        'bg-green-100': task.completed,
        'bg-gray-100': !task.completed,
      }"
    >
      <h2 class="my-2 text-2xl font-semibold">{{ task.title }}</h2>
      <button class="rounded bg-red-200 px-4">Delete</button>
    </div>
  </div>
</template>
