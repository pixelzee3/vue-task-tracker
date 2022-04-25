<script setup>
import { ref } from 'vue';
import TaskList from './TaskList.vue';
import AddTask from './AddTask.vue';

const tasks = ref([
  {
    id: 1,
    title: 'Task 1',
    completed: true,
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
  tasks.value = tasks.value.map(task => {
    if (task.id === taskID) {
      task.completed = !task.completed;
    }
    return task;
  });
}

function deleteTask(taskID) {
  tasks.value = tasks.value.filter(task => task.id !== taskID);
}

function addTask(taskName) {
  console.log(`Adding task: ${taskName}`);
  const taskID = tasks.value.reduce((maxID, task) => Math.max(maxID, task.id), 0) + 1;
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
  <div>
    <h1 class="mt-8 text-center text-4xl font-bold">Task Tracker</h1>
    <div class="border-t-2 rounded mx-8 my-4"></div>
    <AddTask @add="addTask"></AddTask>
    <div class="border-t-2 rounded mx-8 my-4"></div>
    <TaskList :tasks="tasks" @complete="completeTask" @delete="deleteTask" />
  </div>
</template>
