<script setup>
import { ref } from 'vue';

const taskName = ref('');
</script>
<template>
  <div>
    <form
      class="flex justify-between space-x-4"
      @submit.prevent="taskName ? $emit('add', taskName) : null"
    >
      <input
        class="w-full grow bg-slate-100 p-2 md:text-2xl"
        type="text"
        v-model="taskName"
      />
      <input
        type="submit"
        value="Add"
        class="rounded bg-blue-100 px-4 md:px-6 md:text-2xl"
      />
    </form>
  </div>
</template>
