<script setup>
import { ref } from 'vue'
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
    <div class="slider-bar" >
        <div class="background">
            <div v-for="item in data" :key="item.router">
                <a href="">{{ item.title }}</a>
            </div>
        </div>
    </div>
</template>


<style scoped>
    .slider-bar{
        background-color: rgb(34, 34, 34);
        height: 100vh;
    }
    .background{
        background: linear-gradient(190deg,#E9A9FF,#5585FF);
        display: flex;
        flex-direction: column;
        gap: 3px;
        padding-bottom: 3px;
        overflow-x: hidden;
    }
    .slider-bar .background a{
        display: block;
        background-color: rgb(39, 39, 39);
        color: white;
        font-size: 20px;
        text-decoration: none;
        font-weight: bold;
        border: 5px solid transparent;
        padding: 10px;
        transition: transform 0.5s ;
    }
    .slider-bar .background a:hover{
        transform: translateX(20px);
    }

    
</style>