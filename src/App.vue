<script setup>
import { ref } from 'vue';
import TaskList from './TaskList.vue';
import AddTask from './AddTask.vue';
import SeparatorComponent from './SeparatorComponent.vue';

const tasks = ref([
  {
    id: 1,
    title: 'Task 1',
    completed: false,
  },
  {
    id: 2,
    title: 'Task 2',
    completed: false,
  },
  {
    id: 3,
    title: 'Task 3',
    completed: false,
  },
]);

function completeTask(taskID) {
  tasks.value = tasks.value.map((task) => {
    if (task.id === taskID) {
      task.completed = !task.completed;
    }
    return task;
  });
}

function deleteTask(taskID) {
  tasks.value = tasks.value.filter((task) => task.id !== taskID);
}

function addTask(taskName) {
  const taskID =
    tasks.value.reduce((maxID, task) => Math.max(maxID, task.id), 0) + 1;
  tasks.value = [
    ...tasks.value,
    {
      id: taskID,
      title: taskName,
      completed: false,
    },
  ];
}
</script>
<template>
  <div class="pt-8 px-8">
    <h1 class="text-center text-4xl font-bold md:text-6xl">
      Task Tracker
    </h1>
    <SeparatorComponent />
    <AddTask @add="addTask"></AddTask>
    <SeparatorComponent />
    <TaskList :tasks="tasks" @complete="completeTask" @delete="deleteTask" />
  </div>
</template>
