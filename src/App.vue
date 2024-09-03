
<script setup>
import VoacabularySet from './components/VoacabularySet.vue'
import SliderBar from './components/SliderBar.vue';
import EditBox from './components/EditBox.vue';
</script>


<template>
  <header>
  </header>
  <body>
    <div class="left-side">
      <SliderBar />
    </div>
    <div class="right-side">
      <VoacabularySet />
      <EditBox />
    </div>
  </body>
  
</template>

<style scoped>
    body{
      display: flex;
    }
    .left-side{
      width: 300px;
    }
    .right-side{
      width: calc(100% - 300px);
      padding: 10px;
    }

</style>
