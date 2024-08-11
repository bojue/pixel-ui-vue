<template>
  <SubTitle text="按照类型"/>
  <div class="sub-content">
    <PUButton text="默认按钮" type="default"></PUButton>
    <PUButton text="主要按钮" type="primary"></PUButton>
    <PUButton text="成功按钮" type="success"></PUButton>
    <PUButton text="警告按钮" type="warning"></PUButton>
    <PUButton text="错误按钮" type="error"></PUButton>
  </div>
  <SubTitle text="辅助类型"/>
  <div class="sub-content">
    <PUButton text="辅助按钮" type="auxiliary"></PUButton>
    <PUButton text="辅助按钮" type="auxiliary" disabled></PUButton>
  </div>
  <SubTitle text="线框按钮"/>
  <div class="sub-content">
    <PUButton text="主要按钮" type="primary" plain></PUButton>
    <PUButton text="成功按钮" type="success" plain></PUButton>
    <PUButton text="警告按钮" type="warning" plain></PUButton>
  </div>
  <SubTitle text="含自定义图标"/>
  <div class="sub-content">
    <PUButton text="铺满" type="primary" loading></PUButton>
  </div>
  <SubTitle text="按钮形状"/>
  <div class="sub-content">
    <PUButton text="默认按钮" type="primary" ></PUButton>
    <PUButton text="圆角按钮" type="success" rounded></PUButton>
    <PUButton text="圆形按钮" type="warning" circle></PUButton>
  </div>
  <SubTitle text="加载按钮"/>
  <div class="sub-content">
    <PUButton text="铺满" type="primary" loading></PUButton>
  </div>

  <SubTitle text="禁用按钮"/>
  <div class="sub-content">
    <PUButton text="主要按钮" type="primary" disabled></PUButton>
    <PUButton text="成功按钮" type="success" disabled></PUButton>
    <PUButton text="警告按钮" type="warning" disabled></PUButton>
  </div>
  <SubTitle text="按钮大小"/>
  <div class="sub-content">
    <PUButton text="默认按钮" type="primary" size="default"></PUButton>
    <PUButton text="小号按钮" type="success" size="small"></PUButton>
    <PUButton text="迷你按钮" type="warning" size="mini"></PUButton>
    <PUButton text="大号按钮" type="error" plain size="large"></PUButton>
  </div>
  <SubTitle text="按钮宽度"/>
  <div class="sub-content">
    <PUButton text="铺满" type="primary" width="full"></PUButton>
    <PUButton text="一半" type="success" width="half"></PUButton>
    <PUButton text="三分之一" type="error" width="third"></PUButton>
  </div>
  <SubTitle text="块级元素"/>
  <div class="sub-content">
    <PUButton text="块级元素" type="primary" size="default" block></PUButton>
  </div>
  <SubTitle text="自定义颜色"/>
  <div class="sub-content">
    <PUButton text="单色按钮" color="#7232dd"></PUButton>
    <PUButton text="单色线框" color="#7232dd" plain></PUButton>
    <PUButton text="渐变按钮" color="linear-gradient(to right, #4bb0ff, #6149f6)"></PUButton>
  </div>
</template>
<script setup>
import { ref, computed } from 'vue'
import SubTitle from '@/components/comps/SubTitle.vue'
import PUButton from '@/components/lib/Button.vue'

</script>

<style scoped>


.sub-content {
padding: 10px 12px;
background: #fff;

> * {
  margin-right: 15px;
  margin-bottom: 15px;
  }
}

</style>
