<script setup>
import { ref } from 'vue'
const props = defineProps({
  selectList: {
    selectList: Array,
    default: []
  },
  style: {
    type: String,
    default: "width:50px"
  },
  columnName:{
    type: String
  },
  item:{

  }
});
const emit = defineEmits(['changeEvent']);

console.log(props.item);
const isShow = ref(false);
const clickEvent = ()=>{
    isShow.value = !isShow.value;  
}
const listClickEvent = (e) =>{
    const {item} = props;
    emit('changeEvent',item,e.target.innerText);
}
</script>

<template>
    <div :style="style" class="dropdown">
        <span class="select-item">{{ item[columnName] }}</span>
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24" fill="currentColor" class="down-arrow-icon" @click="clickEvent">
            <path d="M7 10l5 5 5-5H7z"/>
        </svg>
        <div class="list" :style="isShow ? '' : 'display:none'">
            <div v-for="item in props.selectList" :id="item.value" @click="listClickEvent" >
                {{ item.text }}
            </div>
        </div>
    </div>


</template>
<style scoped>
    .dropdown{
        display: flex;
        align-items: center;
        position: relative;
    }
    .select-item{
        font-size: 18px;
        min-width: 30px;
    }
    .down-arrow-icon{
        position: relative;
        cursor: pointer;
    }
    .list {

        position: absolute;
        top: 25px;
        left: 0px;
        background-color: rgb(25, 25, 25);
        min-width: 50px;
        z-index: 20;
    }
    .list div{
        padding: 1px 5px;
        font-size: 18px;
        border-bottom: 1px solid rgb(117, 117, 117);
        cursor: pointer;
    }

</style>