<template>
    <div>
     <button >{{text}}</button>
    </div>
</template>

<script>
    export default {
        props:{
            text:String,
            color:String
        }
    }
</script>

<style lang="css" scoped>
button{
    border: none;
    background-color: skyblue;
    padding: 10px 15px;
    font-size: 20px;
    color: darkblue;
    border-radius: 5px;
    cursor: pointer;
}

</style>