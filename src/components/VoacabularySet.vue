<script setup>
    import { ref } from 'vue'
    const data = [
        {
            id : 1,
            title:"product",
            finished:18,
            total:20,
        },
        {
            id : 2,
            title:"product",
            finished:18,
            total:20,
        },
        {
            id : 3,
            title:"product",
            finished:18,
            total:20,
        }
    ]
    const refData = ref(data)
    

</script>
  
<template>
    <div class="vochabulary-section" >
        <div class="vochabulary-set" v-for="item in data" :key="item.id">
            <p class="title">
                {{ item.title }}
            </p>
            <div class="content">
                <div class="icon-section">
                    <div>
                        <div class="keyborad background-1">

                        </div>
                        <div class="puzzle  background-2">
                            
                        </div>
                    </div>
                    <div>
                        <div class="edit  background-1">
                            
                        </div>
                        <div class="bin  background-2">

                        </div>
                    </div>
                </div>
                <p class="complete-rate">
                    <span>{{item.finished}}</span>
                    <span>/</span>
                    <span>{{item.total}}</span>
                </p>
            </div>
        </div>
        <div class="vochabulary-set">
            <span>+</span>
        </div>
    </div>
  </template>
  
<style scoped>
    .vochabulary-section{
        display: flex;
        padding: 5px;
        flex: 70%;
        border-radius: 18px;
        background-color: rgb(50,50,50);
        gap: 18px;
    }
    .vochabulary-set{
        display: flex;
        flex-direction: column;
        border-radius: 15px;
        width: 200px;
        background-color: rgb(42, 42, 42);
        align-items: center;
        padding-top: 15px;
    }  
    .vochabulary-set .title{
        background: linear-gradient(45deg,#E9A9FF,#5585FF);
        border-radius: 18px;
        text-align: center;
        color: white;
        font-size: 18px;
        padding: 3px 0px;
        width: 90%;
        font-weight: bold;
    }
    .vochabulary-set .content{
        display: flex;
        width: 80%;
        justify-content: space-between;
        margin-top: 5px;
        position: relative;
    }
    .vochabulary-set .content > div{
        width: 50%;
    }
    .vochabulary-set .icon-section{
        gap: 8px;
        display: flex;
        padding-top: 5px;
    }
    .vochabulary-set .icon-section div{
        display: flex;
        flex-direction: column;
        gap:8px
    }
    .vochabulary-set .icon-section div > div{
        background-color: rgb(188, 188, 188);
        
    }
    .vochabulary-set .icon-section img{
        width: 25px;
        height: 25px;
    }
    .complete-rate{
        font-size: 22px;
        align-self: flex-end;
        color: white;
        margin-bottom: -10px;
    }
    .vochabulary-set:last-child{
        text-align: center;
        vertical-align: middle;
        font-weight: bold;
        background: linear-gradient(#2f2f2f, #2f2f2f) padding-box, linear-gradient(45deg, #E9A9FF,#5585FF) border-box;
        border: 2px solid transparent;
        cursor: pointer;
    }
    .vochabulary-set:last-child:hover{
        background: linear-gradient(#535353, #535353) padding-box, linear-gradient(45deg, #E9A9FF,#5585FF) border-box;
    }
    .vochabulary-set:last-child span{
        font-size: 70px;
        background: linear-gradient(45deg,#E9A9FF,#5585FF);
        -webkit-text-fill-color: transparent;
        -webkit-background-clip: text;
        padding: 0px;
        
    } 
    .complete-rate span:first-child{
        color: #E9A9FF;
    } 
    .keyborad{
        -webkit-mask-image: url(./icons/keyboard.png);
        -webkit-mask-position: center center;
        -webkit-mask-size: contain;
        -webkit-mask-repeat: no-repeat;
    }
    .puzzle{
        -webkit-mask-image: url(./icons/approval.png);
        -webkit-mask-position: center center;
        -webkit-mask-size: contain;
        -webkit-mask-repeat: no-repeat;
    }
    .edit{
        -webkit-mask-image: url(./icons/edit.png);
        -webkit-mask-position: center center;
        -webkit-mask-size: contain;
        -webkit-mask-repeat: no-repeat;
    }
    .bin{
        -webkit-mask-image: url(./icons/bin.png);
        -webkit-mask-position: center center;
        -webkit-mask-size: contain;
        -webkit-mask-repeat: no-repeat;
    }
    .background-1,.background-2{
        width: 25px;
        height: 25px;
        cursor: pointer;
    }
    .background-1{        
        background: linear-gradient(45deg,#E9A9FF,#5585FF);
    }
    .background-2{
        background: linear-gradient(45deg,#E9A9FF,#5585FF);
    }
    
</style>
