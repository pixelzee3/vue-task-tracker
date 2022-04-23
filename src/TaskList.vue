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
      class="mt-4 rounded-lg px-2 py-4 first:mt-0"
      :class="{ 'bg-green-100': task.completed, 'bg-gray-100': !task.completed }"
    >
      <h2 class="text-2xl font-semibold">{{ task.title }}</h2>
    </div>
  </div>
</template>
