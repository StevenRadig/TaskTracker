<template>
    <div class="task__details">
        <h2 class="task__name">
            {{ task.text }}
            <svg @click="$emit('delete-task')" xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 12 12" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-x">
                <line x1="12" y1="0" x2="0" y2="12"></line>
                <line x1="0" y1="0" x2="12" y2="12"></line>
            </svg>
        </h2>
        <p class="task__day">{{ task.day }}</p>
    </div>
</template>

<script>
    export default {
        name: 'Task',
        props: {
            task: Object
        },
    }
</script>