<template>
    <div :key="task.id" v-for="task in tasks">
        <!-- here we refer to Task's emitted id -->
        <Task @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)" :task="task"/>
    </div>
</template>

<script>
    import Task from './Task'

    export default{
        name: 'Taks',
        props: {
            tasks: Array
        },
        components: {
            Task
        },
        //simply an array of events we are emitting
        emits: ['delete-task', 'toggle-reminder'],
    }
</script>