<template>
  <SubTitle text="默认文本"/>
  <div class="sub-content">
    <PUText text="默认文本样式"></PUText>
  </div>
  <SubTitle text="按照类型"/>
  <div class="sub-content">
    <PUText text="主要" type="primary"></PUText>
    <PUText text="成功" type="success"></PUText>
    <PUText text="警告" type="warning"></PUText>
    <PUText text="危险" type="danger"></PUText>
    <PUText text="默认" type="info"></PUText>
  </div>
  <SubTitle text="文本大小"/>
  <div class="sub-content">
    <PUText text="大号文本" size="large"></PUText>
    <PUText text="默认文本" size="default"></PUText>
    <PUText text="小号文本" size="small"></PUText>
    <PUText text="迷你文本" size="mini"></PUText>
  </div>
  <SubTitle text="姓名脱敏"/>
  <div class="sub-content">
    <PUText mode="name" text="李三四" format="encrypt"></PUText>
  </div>
  <SubTitle text="电话脱敏"/>
  <div class="sub-content">
    <PUText mode="phone" text="15019471110" format="encrypt"></PUText>
  </div>
  <SubTitle text="超链接"/>
  <div class="sub-content">
    <PUText mode="link" text="Go to Github" borderBottom href="https://www.github.com"></PUText>
    <PUText mode="link" text="Go to Github" type="danger" href="https://www.github.com"></PUText>
  </div>
  <SubTitle text="金额格式化"/>
  <div class="sub-content">
    <PUText mode="price" block currency="zh" text="719471110.01"></PUText>
    <PUText mode="price" block currency="en" text="719471110.01"></PUText>
    <PUText mode="price" block currency="enr" text="719471110.01"></PUText>
  </div>
  <SubTitle text="显示行数"/>
  <div class="sub-content">
    <PUText 
      overflow="ellipsis"
      lines="2"
      text="前端组件是用户界面（UI）中的可复用、独立的模块。它们就像搭积木一样，可以组合成复杂的页面。每个组件都有自己的功能、样式和行为，可以被多次使用，从而提高开发效率，降低维护成本。"></PUText>

    <PUText 
      overflow="ellipsis"
      lines="3"
      text="前端组件是用户界面（UI）中的可复用、独立的模块。它们就像搭积木一样，可以组合成复杂的页面。每个组件都有自己的功能、样式和行为，可以被多次使用，从而提高开发效率，降低维护成本。"></PUText>
  </div>
  <SubTitle text="超出设置"/>
  <div class="sub-content">
    <PUText 
      overflow="ellipsis"
      lines="2"
      text="前端组件是用户界面（UI）中的可复用、独立的模块。它们就像搭积木一样，可以组合成复杂的页面。每个组件都有自己的功能、样式和行为，可以被多次使用，从而提高开发效率，降低维护成本。"></PUText>
    <PUText 
      overflow="scroll"
      lines="3"
      text="前端组件是用户界面（UI）中的可复用、独立的模块。它们就像搭积木一样，可以组合成复杂的页面。每个组件都有自己的功能、样式和行为，可以被多次使用，从而提高开发效率，降低维护成本。"></PUText>

    <PUText 
      overflow="auto"
      text="前端组件是用户界面（UI）中的可复用、独立的模块。它们就像搭积木一样，可以组合成复杂的页面。每个组件都有自己的功能、样式和行为，可以被多次使用，从而提高开发效率，降低维护成本。"></PUText>
  </div>
  <SubTitle text="自定义样式"/>
  <div class="sub-content">
    <PUText text="自定义颜色" color="blue"></PUText>
    <PUText text="自定义尺寸" size="18px"></PUText>
    <PUText text="自定义背景" color="yellowgreen" background="beige"></PUText>

    
  </div>
</template>
<script setup>
import { ref, computed } from 'vue'
import SubTitle from '@/components/comps/SubTitle.vue'
import PUText from '@/components/lib/Text.vue'

const customStyle = ref({
  color: 'rgb(255, 125, 0)',
  borderColor:'rgb(255, 125, 0)'
})

</script>

<style scoped>


.sub-content {
  padding: 10px 20px;
  background: #fff;
  > * {
    margin-bottom: 15px;
    margin-right: 15px;
    &:nth-child(3n) {
      margin-bottom: 0px;
    }
  }
}

</style>
