<template>
  <SubTitle text="按照类型"/>
  <div class="sub-content">
    <PUSwitch :checked="checked" type="primary"></PUSwitch>
    <PUSwitch type="primary" :checked="!checked"></PUSwitch>
  </div>
  <SubTitle text="形状"/>
  <div class="sub-content">
    <PUSwitch rightAngle :checked="checked"></PUSwitch>
    <PUSwitch round :checked="checked"></PUSwitch>
  </div>
  <SubTitle text="文字"/>
  <div class="sub-content">
    <PUSwitch :text="text" :checked="checked"></PUSwitch>
    <PUSwitch :text="textZH" :checked="checked"></PUSwitch>
  </div>
  <SubTitle text="大小"/>
  <div class="sub-content">
    <PUSwitch size="default" :checked="checked"></PUSwitch>
    <PUSwitch size="default" rightAngle :checked="!checked"></PUSwitch>
    <PUSwitch size="small" :text="textZH" :checked="checked"></PUSwitch>
    <PUSwitch size="small" :text="textZH" rightAngle :checked="!checked" ></PUSwitch>
  </div>
  <SubTitle text="自定义大小"/>
  <div class="sub-content">
    <PUSwitch size="32px" :checked="checked"></PUSwitch>
    <PUSwitch size="26px" :checked="checked" rightAngle></PUSwitch>
    <PUSwitch size="20px" :checked="checked" ></PUSwitch>
  </div>
  <SubTitle text="自定义颜色"/>
  <div class="sub-content">
    <PUSwitch active-color="rgb(52, 199, 89)" :checked="checked"></PUSwitch>
    <PUSwitch active-color="darkcyan" rightAngle inactive-color="thistle" :checked="!checked"></PUSwitch>
  </div>
</template>
<script setup>
import { ref, computed } from 'vue'
import SubTitle from '@/components/comps/SubTitle.vue'
import PUSwitch from '@/components/lib/Switch.vue'

const checked= ref(true)
const text = ref({
  on: "ON",
  off: "OFF"
})

const textZH = ref({
  on: "开",
  off: "关"
})

const changeState = () => {
  checked.value = !checked.value
}

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
