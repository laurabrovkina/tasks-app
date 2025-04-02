<script lang="ts" setup>
import { ref } from 'vue';
import type { Task } from './types';
import TaskForm from './components/TaskForm.vue';
import TaskList from './components/TaskList.vue';

const message = ref("Tasks App");
const tasks = ref<Task[]>([]);

function addTask(newTask: string) {
  tasks.value.push({
    id: crypto.randomUUID(),
    title: newTask,
    done: false
  })
}
</script>

<template>
  <main>
    <h1>{{ message }}</h1>
    <TaskForm @add-task="addTask" />
    <h3 v-if="!tasks.length">Add a task to get started.</h3>
    <h3 v-else> 0 / {{ tasks.length }} tasks completed</h3>
    <TaskList :tasks="tasks" />
  </main>
</template>

<style>
main {
  max-width: 800px;
  margin: 1rem auto;
}


.button-container{
  display: flex;
  justify-content: end;
}
</style>