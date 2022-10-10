<template>
    <div class="form-submit">
      <form @submit.prevent="handleSubmit">
        <label  for="work">Work: </label>
        <input type="text" placeholder="Meeting with Boss" v-model="work">
        <label  for="date">Date: </label>
        <input type="date" placeholder="21-11-2022" v-model="date">
        <label  for="time">Time: </label>
        <input type="text" placeholder="3:30PM" v-model="time">
        <ul>
        <li>
        <label  for="priyority">Reminder </label>
        <input type="checkbox" v-model="reminder">
        </li>
        <li>
        <label  for="priyority">High Priyority </label>
        <input type="checkbox" v-model="priyority">
        </li>
        </ul>
        <button class="submit" type="submit" >submit</button>
      </form>
    </div>
</template>

<script>
export default {
    data(){
        return{
            work:'',
            date:'',
            time:'',
            reminder:false,
            priyority:false
        }
    },
    methods:{
        handleSubmit(){
            const task={
                id:Math.floor(Math.random()*10000000),
                work:this.work,
                date:this.date,
                time:this.time,
                reminder:this.reminder,
                highPriyority:this.priyority
            }
            fetch('https://lively-earmuffs-worm.cyclic.app/todo',{
                method:"POST",
                headers:{
                    'content-type':'application/json'
                },
                body:JSON.stringify(task)
            })
            .then(res=>res.json())
            .then(data=>{
                if(data.success){
                    alert("Task added successfully")
                    this.$emit("add-task",task)
                }
            })

            this.work='';
            this.date='';
            this.time='';
            this.reminder=false;
            this.priyority=false;
        }
    }
}
</script>

<style lang="css" scoped>
.form-submit label{
    display: block;
    font-size: 25px;
    font-weight: 800;
    line-height: 40px;
}
.form-submit label:last-child{
    display: inline !important;
}
.form-submit input{
    display: block;
    width: 90%;
    background: white;
    border: 1px solid gray;
    border-radius: 6px;
    padding: 10px;
}

.form-submit ul{
    display: flex;
    flex-direction: row;
    width: 90%;
    justify-content: space-around;
    align-items: center;
    box-sizing: border-box;
}
.form-submit li{
    list-style: none;
    display: flex;
    align-items: center;
}
.form-submit input:last-child{
    display: inline !important;
    width: 20px;
    line-height: 40px;
}
.submit{
    font-size: 25px;
    background: skyblue;
    padding: 15px 20px;
    border: none;
    cursor: pointer;
    width: 94%;
    border-radius: 3px;
}
</style>