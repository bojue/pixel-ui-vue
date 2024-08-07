<template>
   <SubTitle text="基础用法"/>
    <div class="sub-content">
      <PUDivider />
      <PUDivider type="strip"/>
    </div>
    <SubTitle text="内容"/>
    <div class="sub-content">
      <PUDivider text="文本"/>
    </div>
    <SubTitle text="类型"/>
    <div class="sub-content">
      <PUDivider text="默认" type="solid"/>
      <PUDivider text="虚线" type="dashed"/>
      <PUDivider text="点线" type="dotted"/>
      <PUDivider text="条状" type="strip"/>
    </div>

    <SubTitle text="粗细"/>
    <div class="sub-content">
      <PUDivider text="细线" thin/>
      <PUDivider text="默认" />
      <PUDivider text="粗线" bold/>
    </div>
    <SubTitle text="内容大小"/>
    <div class="sub-content">
      <PUDivider text="大号文本" size="large"/>
      <PUDivider text="默认文本" size="default"/>
      <PUDivider text="小号文本" size="small"/>
      <PUDivider text="最小号文本" size="mini"/>
    </div>
    <SubTitle text="自定义宽度"/>
    <div class="sub-content">
      <PUDivider text="50px" width="50px"/>
      <PUDivider text="20%" width="20%"/>
    </div>

    <SubTitle text="自定义样式"/>
    <div class="sub-content">
      <PUDivider color="#07c160" text="自定义颜色"/>
      <PUDivider contentColor="#165DFF" borderColor="#165DFF" borderStyle="dashed" text="自定义类型"/>
      <PUDivider 
        background="linear-gradient(to right, blue, pink)" 
        height="10px" 
        color="#ffffff" 
        type="strip" 
        text="自定义背景"/>
    </div>


</template>
<script setup>
import { ref, computed } from 'vue'
import SubTitle from '@/components/comps/SubTitle.vue'
import PUDivider from '@/components/lib/Divider.vue'

</script>

<style scoped>


.sub-content {
  padding: 10px 20px;
  background: #fff;
  > * {
    margin-bottom: 15px;
    &:nth-child(3n) {
      margin-right: 0px;
    }
  }
}

</style>
