<script lang="ts" setup>
import type { Task } from "../types";

const props = defineProps<{
    tasks: Task[]
}>();

const emits = defineEmits<{
    toggleDone: [id: string]
}>();
</script>

<template>
    <div class="task-list">
        <article v-for="task in props.tasks" :key="task.id">
            <label>
                <input 
                @input="emits('toggleDone', task.id)"
                :checked="task.done" type="checkbox"
                >
                {{ task.title }}
            </label>
        </article>
    </div>
</template>

<style>
.task-list{
    margin-top: 1rem;
}
</style>