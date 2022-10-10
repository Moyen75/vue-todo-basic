<template>
    <div class="todo-list">
   <Todo :todos="todos"></Todo>
  </div>
</template>

<script>
import Todo from './Todo.vue';
export default {
   props:{
    todos:Array
   },
   components:{
    Todo
   },
}
</script>

<style lang="css" scoped>

</style>