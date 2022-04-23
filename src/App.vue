<script setup>
import { ref } from 'vue';
import TaskList from './TaskList.vue';

const tasks = ref([]);
</script>
<template>
  <div>
    <h1 class="mt-8 text-center text-4xl font-bold">Task Tracker</h1>
    <TaskList :tasks="tasks" />
  </div>
</template>
