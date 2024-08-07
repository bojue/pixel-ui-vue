<template>
  <SubTitle text="按照类型"/>
  <div class="sub-content">
    <PUTag text="默认" type="default"></PUTag>
    <PUTag text="主要" type="primary"></PUTag>
    <PUTag text="成功" type="success"></PUTag>
    <PUTag text="警告" type="warning"></PUTag>
    <PUTag text="错误" type="error"></PUTag>
  </div>
  <SubTitle text="线框"/>
  <div class="sub-content">
    <PUTag text="主要" type="primary" plain></PUTag>
    <PUTag text="成功" type="success" plain></PUTag>
    <PUTag text="警告" type="warning" plain></PUTag>
  </div>
  <SubTitle text="浅色"/>
  <div class="sub-content">
    <PUTag text="默认" type="default" light></PUTag>
    <PUTag text="主要" type="primary" light></PUTag>
    <PUTag text="成功" type="success" light></PUTag>
    <PUTag text="警告" type="warning" light></PUTag>
    <PUTag text="错误" type="error"   light></PUTag>
  </div>
  <SubTitle text="浅色线框"/>
  <div class="sub-content">
    <PUTag text="默认" type="default" plain light></PUTag>
    <PUTag text="主要" type="primary" plain light></PUTag>
    <PUTag text="成功" type="success" plain light></PUTag>
    <PUTag text="警告" type="warning" plain light></PUTag>
    <PUTag text="错误" type="error"   plain light></PUTag>
  </div>
  <SubTitle text="形状"/>
  <div class="sub-content">
    <PUTag text="默认" type="primary" ></PUTag>
    <PUTag text="圆角" type="success" fillet></PUTag>
    <PUTag text="圆形" type="warning" rounded></PUTag>
  </div>

  <SubTitle text="大小"/>
  <div class="sub-content">
    <PUTag text="大号" type="primary" size="large"></PUTag>
    <PUTag text="默认" type="success" size="default"></PUTag>
    <PUTag text="小号" type="warning" size="small"></PUTag>
    <PUTag text="迷你" type="error"  size="mini"></PUTag>
  </div>
  <SubTitle text="超过隐藏"/>
  <div class="sub-content">
    <PUTag :text="text" type="primary" width="100px"></PUTag>
  </div>
  <SubTitle text="自定义颜色"/>
  <div class="sub-content">
    <PUTag text="单色背景" color="#7232dd"></PUTag>
    <PUTag text="单色线框" color="#7232dd" plain></PUTag>
    <PUTag text="渐变背景" color="linear-gradient(to right, #4bb0ff, #6149f6)"></PUTag>
  </div>
</template>
<script setup>
import { ref, computed } from 'vue'
import SubTitle from '@/components/comps/SubTitle.vue'
import PUTag from '@/components/lib/Tag.vue'

const text = '前端组件是用户界面（UI）中的可复用、独立的模块。它们就像搭积木一样，可以组合成复杂的页面。每个组件都有自己的功能、样式和行为，可以被多次使用，从而提高开发效率，降低维护成本'

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
