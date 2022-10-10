<template>
    <div class="form-submit">
      <form @submit.prevent="handleSubmit">
        <label  for="work">Work </label>
        <input type="text" v-model="work">
        <label  for="date">Date </label>
        <input type="text" v-model="date">
        <label  for="time">Time </label>
        <input type="text" v-model="time">
        <li>
        <label  for="priyority">High Priyority </label>
        <input type="checkbox" v-model="priority">
        </li>
        <button class="submit" type="submit" >submit</button>
      </form>
    </div>
</template>

<script>
export default {
    data(){
        return{
            work:'',
        }
    },
    methods:{
        handleSubmit(){
            const task={
                work:this.work,
                id:Math.floor(Math.random()*10000000000000)
            }
            this.$emit('add-task',task)
            this.work=''
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

.form-submit input:last-child{
    display: inline !important;
    width: 19px;
}
.form-submit li{
    list-style: none;
    display: flex;
    align-items: center;
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