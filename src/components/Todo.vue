<template>
  <div class="todo-list">
   <ul class="todos" :key="todo.id" v-for="todo in todos">
    <li class="todo" >{{todo.work}}</li>
   </ul>
  </div>
</template>

<script>
export default {
    props:{
        todos:Array
    }
}
</script>

<style scoped>

.todos{
    list-style: none;
}
.todo{
    background-color: antiquewhite;
    border-radius: 5px;
    padding: 10px 15px;
}
</style>