<script setup>
  import { ref } from 'vue';

  const taskName = ref('');
</script>
<template>
  <div class="mx-8">
    <form class="flex justify-between space-x-4">
      <input class="bg-slate-100 p-2 w-full grow" type="text" :v-model="taskName">
      <button class="bg-blue-100 px-4 rounded ">Add</button>
    </form>
  </div>
</template>
