<template>
    <div class="task-list">
        <div :class="task.reminder ? 'task task--reminder' : 'task'" :key="task.id" v-for="task in tasks">
            <Task 
                :task="task"
                @dblclick="$emit('toggle-reminder', task.id)" 
                @delete-task="$emit('delete-task', task.id)" 
            />
        </div>
    </div>
</template>

<script>
    import Task from './Task'

    export default {
        name: 'Tasks',
        props: {
            tasks: Array,
        },
        components: {
            Task
        },
        emits: ['toggle-reminder', 'delete-task'],
    }
</script>