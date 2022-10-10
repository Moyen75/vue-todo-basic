<template>
    <div class="todo-list">
   <Todo ></Todo>
  </div>
</template>

<script>
import Todo from './Todo.vue';
export default {
   props:{
      tasks:{
         type:Array,
         required:true
      }
   },
   components:{
    Todo
   },
}
</script>

<style lang="css" scoped>

</style>