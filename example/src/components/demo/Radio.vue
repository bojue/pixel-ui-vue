<template>
  <SubTitle text="按照类型"/>
  <div class="sub-content">
    <PURadioGroup 
      :v-mode="value" 
      :data="groupDataList"
      labelField="name"
      valueField="value"
    />
  </div>
</template>
<script setup>
import { ref, computed } from 'vue'
import SubTitle from '@/components/comps/SubTitle.vue'
import PURadioGroup from '@/components/lib/Radio.vue'

const title = "你最喜欢的公司？"
const value='Google'
const groupDataList = [{
  name: '苹果',
  value: 'Apple'
}, {
  name: '微软',
  value: 'Microsoft'
}, {
  name: '谷歌',
  value: 'Google'
}]

</script>

<style scoped>


.sub-content {
padding: 10px 20px;
background: #fff;

> * {
  margin-right: 15px;
  margin-bottom: 15px;
  }
}


</style>
