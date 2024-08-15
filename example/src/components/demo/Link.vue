<template>
  <SubTitle text="默认"/>
  <div class="sub-content">
    <PULink href="https://github.com/bojue" text="Pixel-UI 组件库"></PULink>
  </div>
  <SubTitle text="底部下划线"/>
  <div class="sub-content">
    <PULink href="https://github.com/bojue" text="Pixel-UI 组件库" underline></PULink>
  </div>
  <SubTitle text="自定义文本内容"/>
  <div class="sub-content">
    <PULink href="https://github.com/bojue" text="Pixel-UI Github 组件库"></PULink>
  </div>
  <SubTitle text="自定义颜色"/>
  <div class="sub-content">
    <PULink href="https://github.com/bojue" text="Pixel-UI 组件库" color="#07c160"></PULink>
  </div>
  <SubTitle text="自定义背景色"/>
  <div class="sub-content">
    <PULink href="https://github.com/bojue" 
      text="超级链接背景色" 
      background="beige"
      color="#64748b"
      underline
    ></PULink>
  </div>


</template>
<script setup>
import { ref, computed } from 'vue'
import SubTitle from '@/components/comps/SubTitle.vue'
import PULink from '@/components/lib/Link.vue'

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
