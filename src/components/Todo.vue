<template>
  <div class="todo-list">
   <div class="table-box">
    <div class="table-row head">
         <div class="table-cell">
            <p>Task</p>
         </div>
         <div class="table-cell">
            <p>Date</p>
         </div>
         <div class="table-cell">
            <p>Time</p>
         </div>
    </div>
    <div :class="[todo.highPriyority ? 'table-row priyority':'table-row'] " @dblclick="deleteTask(todo.id)" :key="todo.id" v-for="todo in tasks">
         <div class="table-cell">
            <p>{{todo.work}}</p>
         </div>
         <div class="table-cell">
            <p>{{todo.date}}</p>
         </div>
         <div class="table-cell reminder">
            <p >{{todo.time}}</p>
            <i v-if="todo.reminder" class="fa-solid fa-bell"></i>
         </div>
    </div>
   </div>
  </div>
</template>

<script>
export default {
    props:{
        tasks:Array
    },
    methods:{
        async deleteTask(id){
            await fetch(`https://lively-earmuffs-worm.cyclic.app/todo/${id}`,{
                method:"PUT",
                headers:{
                    'content-type':"application/json"
                },
                body:JSON.stringify({isDeleted:true})
            })
            .then(res=>res.json())
            .then(data=>{
                if(data.updated.modifiedCount >0){
                    alert("Task deleted successfully");
                    this.$emit("task-delete",id)
                }
            }
            )
        }
    }
}
</script>

<style scoped>
.todo-list{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.todos{
    list-style: none;
    box-sizing: border-box;
    padding: 10px;
    width: 94%;
    margin-top: 10px;
}
.table-box{
    margin: auto;
}
.table-row{
    width: 93.5%;
    background: transparent;
    color: #555;
    min-height: 80px;
    border-radius: 5px;
    box-shadow: 0 1px 4px 0 rgb(0, 20, 50,0.3);
    margin:10px 0;
    box-sizing: border-box;
    display: flex;
}
.table-cell{
    display: table-cell;
    text-align: center;
    width: 40%;
    padding: 10px;
    border-right: 1px solid #d6d4d4;
    vertical-align: middle;
    box-sizing: border-box;
}
.table-cell:last-child{
    border: none;
}
.head{
    background-color: #33AFFF;
    color: white;
}
.priyority{
    position: relative;
}
.priyority::after{
     position: absolute;
     content: "";
     background-color: #9133FF;
     top: 0;
     left: 0;
     bottom: 0;
     width: 6px;
     height: 100%;
     border-radius: 5px 0 0 5px;
     z-index: 1;
}
.reminder{
    position: relative;
    overflow: hidden;
    box-sizing: border-box;
}

.reminder .fa-bell{
    position: absolute;
    width: 30px;
    top: -2px;
    right: -22px;
    color: #33F7FF;
    transform: rotate(45deg);
    background-color: #9133FF;
    padding:5px 20px;
}

</style>