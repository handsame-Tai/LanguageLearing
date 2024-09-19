<script setup>
import { ref ,computed} from 'vue'
import Dropdown from './share/Dropdown.vue';
    const VoacabbularyTitle = "product";
    let id = 0;
    const data = ref(
        [
        {
            id:id++,
            voucher:"Home",
            translate:"家",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"Home",
            translate:"家",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"Home",
            translate:"家",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"Home",
            translate:"家",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"Home",
            translate:"家",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"Home",
            translate:"家1",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"Home",
            translate:"幹",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
        {
            id:id++,
            voucher:"description",
            translate:"備註",
        },
    ]);
    const amountPerPage = ref(11);
    const nowPage = ref(0);

    const displayData = computed(()=>{
        const dataCount = data.value.length - 1;
        const starNum = nowPage.value * amountPerPage.value;
        const endNum = starNum +  amountPerPage.value;
        let pairData = [];
        for(let i = starNum ; i < endNum ;i++){
            let leftItem = i > dataCount ? null : data.value[i];
            let rightItem = i + amountPerPage.value > dataCount  ? null : data.value[i + amountPerPage.value]; 
            pairData.push([leftItem,rightItem]);
        }
        return pairData;
    });
    const selectedItem = [
        {
            value:1,
            text:"N"
        },
        {
            value:2,
            text:"V"
        },
        {
            value:3,
            text:"Adj"
        },
        {
            value:4,
            text:"O"
        },
    ];
    const translateData = ref([
        {
            part_of_speech:"N",
            translate:"家",
        },
        {
            part_of_speech:"N",
            translate:"家",
        },
        {
            part_of_speech:"N",
            translate:"家",
        },
        {
            part_of_speech:"N",
            translate:"家",
        },
        {
            part_of_speech:"N",
            translate:"家",
        },
        {
            part_of_speech:"N",
            translate:"家",
        }
    ]);
    const exampleData = ref([
        {
            sentences:"This is my house",
            translate:"這是我的家",
        }
    ]
    ); 
    const changePartOfSpeech = (item,value)=>{
        item.part_of_speech = value;
    }
    const addTranslateEvent = ()=>{
        translateData.value.push(
            {
                part_of_speech:"N",
                translate:"",
            }
        );
    }
    const addVoacabularyEvent = ()=>{
            data.value.push(
                {
                    id:id++,
                    voucher:"description",
                    translate:"備註",
                },
        );
    }
    const shiftpage = (page)=>{
        nowPage.value = page;
    } 
    const page = [0,1,2,3,4];
</script>
<template>
    <div class="edit-content">
        <div class="edit-box" >
            <div class="header">
                <p class="title">{{ VoacabbularyTitle }}</p>
                <span class="add-button" @click="addVoacabularyEvent">
                    +
                </span>
            </div>
            <div class="content">
                <table>
                    <thead>
                        <tr>
                            <td>單字</td>
                            <td>翻譯</td>
                            <td>單字</td>
                            <td>翻譯</td>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="item in displayData" :key="item[0].id">
                            <td v-if="item[0] != null">{{ item[0].voucher }}</td>
                            <td v-if="item[0] != null">{{ item[0].translate }}</td>
                            <td v-if="item[1] != null">{{ item[1].voucher }}</td>
                            <td v-if="item[1] != null">{{ item[1].translate }}</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <footer>
                    <div v-for="item in page" :class="[item === nowPage ? 'circle selected':'circle']" @click="()=>{shiftpage(item)}" :id="item" ></div>
            </footer>
        </div>
        <div class="voacabulary-detail-box" >
            <p class="title">
                Product
            </p>
            <div class="translate-section" >
                <div class="header-section">
                    <p class="section-title">翻譯</p>

                    <div class="button-setion">
                        <div class="button" @click="addTranslateEvent">+</div>
                    </div>
                </div>
                <div class="section-content">
                    <div class="translate-box" v-for="item in translateData">
                        <Dropdown 
                            :selectList="selectedItem" 
                            :item="item" 
                            :columnName="'part_of_speech'"
                            @changeEvent="changePartOfSpeech"></Dropdown>
                        <input type="text" style="width: 70%;" v-model="item.translate"/>
                    </div>
                </div>
            </div>
            <div class="sentences-section" >
                <p class="section-title" >例句</p>
                <div class="section-content">
                    <div class="sentences-box" v-for="item in exampleData">
                        <input type="text" v-model="item.sentences" />
                        <input type="text" v-model="item.translate" />
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>


<style scoped>
    .edit-content{
        display: flex;
        justify-content: space-between;
        margin-top: 20px;
    }
    .edit-box,.voacabulary-detail-box{
        width: 49.5%;
        background-color: rgb(42, 42, 42);
        display: flex;
        flex-direction: column;
        border-radius: 15px;
        padding: 10px;
    }
    .header{
        display: flex;
        justify-content: space-between;
        align-items: flex-end;
    }
    .edit-section{
        display: flex;
        justify-content: space-around;
    }
   .add-button{
        background: linear-gradient(45deg,#E9A9FF,#326bfc);
        color: #326bfc;
        border-radius: 50%;
        font-size: 24px;
        height: 37px;
        width: 37px;
        text-align: center;
        font-weight: bold;
        cursor: pointer;
        color: rgb(255, 255, 255);
        background-color: #E9A9FF;
    }
    .title{
        color: white;
        padding: 5px 40px;
        display: inline-block;
        text-align: center;
        font-size: 18px;
        font-weight: bold;
        border-radius: 12px;
        background-color: rgb(98, 98, 98);
        width:fit-content;
    }
    .borad{
        width: 100%;
        height: 4px;
        background-color: rgb(83, 83, 83);
        margin: 10px 0px;
        border-radius: 12px;
    }
    .content{
        height: 100%;
        gap: 4px;
        display: flex;
    }
    table{
        width: 100%;
        margin-top: 10px;
    }
    thead{
        background-color: hsl(268, 40%, 52%);
    }
    thead td{
        font-weight: bold;
        text-align: center;
        color: white;
        padding: 3px;

    }
    tbody td{
        font-size: 18px;
        width: 25%;
        background-color: rgb(61, 61, 61);
        padding: 7px 10px;
        color: rgb(201, 201, 201);
    }
    .edit-box footer{
        height: 10px;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 20px;
        padding: 20px 0px 10px 0px;
    }
    .edit-box footer .circle{
        width: 8px;
        height: 8px;
        background-color: rgb(152, 152, 152);
        border-radius: 50%;
    }
    .edit-box footer .selected{
        background-color: white;
    }
    .voacabulary-detail-box{
        align-items: center;
    }
    .voacabulary-detail-box .title{
        font-size: 20px;
        padding: 5px 40px;
        background-color: rgb(80,80,80);
        width: fit-content;
    }
    .section-title{
        font-size: 18px;
        font-weight: bold;
    }
    .translate-section{
        width: 100%;
        margin-top: 10px;
    }
    .translate-box{
        width: 33%;
        background-color: rgb(53, 53, 53);
        padding: 3px;
        border: rgb(120, 120, 120) 1px solid;
        display: flex;
    }
    input[type="text"]{
        background-color: transparent;
        border: none;
        font-size: 15px;
        color: white;
    }
    input[type="text"]:focus{
        border: none;
        outline: none;
    }
    .section-content{
        display: flex;
        flex-wrap: wrap;
    }
    .sentences-box{
        width: 100%;
    }
    .sentences-box input[type="text"]{
        width: 100%;
        font-size: 20px;
    }
    .sentences-section{
        width: 100%;
        margin-top: 10px;
    }
    .button-setion .button{
        background-color: rgb(120, 120, 120);
        border-radius: 50%;
        font-size: 18px;
        height: 27px;
        width: 27px;
        text-align: center;
        font-weight: 1000;
        cursor: pointer;
        color: rgb(255, 255, 255);
    }
    .header-section{
        display: flex;
        justify-content: space-between;
        margin-bottom: 5px;
        align-items: center;
    }
    

</style>