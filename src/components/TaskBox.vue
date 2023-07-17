<template>
    <div v-for='task in tasks' :key='task.id'>
        <TaskContent @delete-task="$emit('delete-task', task.id)" @toggle-reminder="$emit('toggle-reminder', task.id)" :task='task'/>
    </div>

</template>

<script>
    import TaskContent from './TaskContent.vue'

    export default {
        name: 'TaskBox',
        props: {
            tasks: Array,
        },
        components:{
            TaskContent,
        },
        emits:['delete-task', 'toggle-reminder']
    }
</script>
