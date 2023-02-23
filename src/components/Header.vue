<template>
    <header>
        <h1>{{title}}</h1>
        <Button @btn-click="$emit('toggle-add-task')" :text="showAddTask ? 'Close' : 'Add Task'" :color="showAddTask ? 'red' : 'green'" />
    </header>
</template>

<script>

//here we import needed comonents to use them
import Button from './Button'

export default{
    name: 'Header',
    //inside props we define our variables, which we will use inside template {{variable name}}
    props: {
        title: String,
        showAddTask: Boolean
    },
    components: {
        Button
    }
}
</script>

<!-- style scoped means that everything that we define here will be only available for
     this Header.vue file -->
<style scoped>
    header{
        display: flex;
        justify-content: space-between;
        align-items:  center;
        margin-bottom: 20px;
    }
</style>