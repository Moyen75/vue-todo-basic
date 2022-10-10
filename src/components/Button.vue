<template>
    <div>
     <button @click="toggleButton" :style="{backgroundColor:bgColor,color:color}">{{text}}</button>
    </div>
</template>

<script>
    export default {
        props:{
            text:String,
            bgColor:String,
            color:String
        },
        methods:{
            toggleButton(){
                this.$emit('toggle-button')
            }
        }
    }
</script>

<style lang="css" scoped>
button{
    border: none;
    padding: 10px 15px;
    font-size: 20px;
    border-radius: 5px;
    cursor: pointer;
}

</style>