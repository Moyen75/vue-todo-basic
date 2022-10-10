<template>
    <div class="main">
        <div class="container">
            <h1>To do</h1>
            <Button @toggle-button="toggleAddTaskButton" v-if="showAddButton" :bgColor="`skyblue`"  :color="`darkblue`" :text="`Add Task`"/>
            <Button @toggle-button="toggleAddTaskButton" v-else :bgColor="`#EF055B`"  :color="`white`"  :text="`Close`"/>
        </div>
        <TaskForm v-if="!showAddButton" @add-task="addTask"/>
        <Todo @task-delete="deleteTask" v-if="todos.length >0" :tasks="todos || []"/>
    </div>
</template>

<script>
import Todo from './Todo.vue';
import TaskForm from './TaskForm.vue';
import Button from './Button.vue'
export default {
    data() {
        return {
            todos: [],
            showAddButton:true
        }
    },
    components:{
        TaskForm,
        Todo,
        Button
    },
    methods:{
        toggleAddTaskButton(){
            this.showAddButton=!this.showAddButton
        },
        deleteTask(id){
            this.todos=this.todos.filter(task=>task.id !==id)
        },
        addTask(task){
            this.todos=[...this.todos,task]
        }
    },
   async created(){
        const res=await fetch('https://lively-earmuffs-worm.cyclic.app/todos/all')
        const data=await res.json();
        this.todos=data.tasks;
    }
}
</script>

<style  scoped>
.main {
    max-width: 540px;
    background-color: #f6f4f4;
    border: 1px solid #cec5c5;
    border-radius: 5px;
    margin: auto;
    padding: 30px;
    box-sizing: border-box;
}

.container {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    box-sizing: border-box;
    
}
.container h1{
    text-align: center;
    font-weight: 900;
    color: darkblue;
}
</style>