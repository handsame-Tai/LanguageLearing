<script setup>
import { ref } from 'vue'
    const VoacabbularyTitle = "product";
    const data = [
        {
            title:"Home",
            router:"./index",
            icon:""
        },
        {
            title:"Voacabbulary Set",
            router:"./index",
            icon:""
        },
        {
            title:"Contact Us",
            router:"./index",
            icon:""
        },
    ]
</script>
<template>
    <div class="edit-content">
        <div class="edit-box" >
            <p class="title">{{ VoacabbularyTitle }}</p>
        
        </div>
        <div class="edit-box" >
            
        </div>
    </div>
</template>


<style scoped>
    .edit-content{
        display: flex;
        justify-content: space-between;
        margin-top: 20px;
    }
    .edit-box{
        width: 48%;
        background-color: rgb(42, 42, 42);
        display: flex;
        flex-direction: column;
        height: 70vh;
        border-radius: 15px;
    }
    .title{
        background: linear-gradient(190deg,#E9A9FF,#5585FF);
        color: white;
        padding: 5px;
        display: inline-block;
    }

    
</style>