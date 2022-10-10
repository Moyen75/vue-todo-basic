<template>
    <div class="main">
        <div class="container">
            <h1>To do</h1>
            <Button :color="green" :text="`Add Task`"/>
        </div>
        <TaskForm/>
    </div>
</template>

<script>
import Todos from './Todos.vue'
import TaskForm from './TaskForm.vue';
import AddTask from './AddTask.vue';
import Button from './Button.vue'
export default {
    data() {
        return {
            todos: [],
            showAddTaskButton:false
        }
    },
    components:{
        TaskForm,
        AddTask,
        Todos,
        Button
    },
    methods:{
        showAddTaskButton(){
            this.showAddTaskButton=!this.showAddTaskButton
        },
        addTask(task){
            this.todos=[...this.todos,task]
            console.log(task)
        }
    }
}
</script>

<style  scoped>
.main {
    max-width: 540px;
    background-color: #f5f5f5;
    border: 1px solid #f9f9f9;
    border-radius: 5px;
    margin: auto;
    padding: 30px;
}

.container {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    
}
.container h1{
    text-align: center;
    font-weight: 900;
    color: darkblue;
}
</style>