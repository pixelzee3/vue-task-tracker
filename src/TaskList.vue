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
      class="delay-50 mt-4 flex justify-between rounded-lg px-2 py-4 transition-all first:mt-0"
      :class="{
        'bg-green-100': task.completed,
        'bg-gray-100': !task.completed,
      }"
      @click="$emit('complete', task.id)"
    >
      <h2 class="my-2 text-2xl font-semibold md:text-4xl">{{ task.title }}</h2>
      <button
        class="rounded bg-red-200 px-4 md:px-6 md:text-2xl"
        @click.stop="$emit('delete', task.id)"
      >
        Delete
      </button>
    </div>
  </div>
</template>
