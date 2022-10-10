<template>
    <div>
        <TaskForm @add-task="addTask"></TaskForm>
    </div>
</template>

<script>
import TaskForm from './TaskForm.vue';
export default {
    components:{
        TaskForm
    },
    methods:{
        addTask(task){
          this.$emit('add-task',task)
      }
    }
}
</script>

<style lang="css" scoped>

</style>