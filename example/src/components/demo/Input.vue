<template>
  <SubTitle text="默认"/>
  <div class="sub-content">
    <PUInput text="默认内容"></PUInput>
  </div>
  <SubTitle text="形状类型"/>
  <div class="sub-content">
    <PUInput placeholder="直角"></PUInput>
    <PUInput placeholder="圆角"></PUInput>
  </div>
  <SubTitle text="可清空内容"/>
  <div class="sub-content">
    <PUInput></PUInput>
  </div>
  <SubTitle text="数字键盘"/>
  <div class="sub-content">
    <PUInput></PUInput>
  </div>
  <SubTitle text="密码类型"/>
  <div class="sub-content">
    <PUInput></PUInput>
  </div>
  
  <SubTitle text="显示下划线"/>
  <div class="sub-content">
    <PUInput ></PUInput>
  </div>
  <SubTitle text="禁止"/>
  <div class="sub-content">
    <PUInput></PUInput>
  </div>
  <SubTitle text="只读"/>
  <div class="sub-content">
    <PUInput></PUInput>
  </div>
  <SubTitle text="前后插槽"/>
  <div class="sub-content">
    <PUInput placeholder="前插槽"></PUInput>
    <PUInput placeholder="后插槽"></PUInput>
  </div>
</template>
<script setup>
import { ref, computed } from 'vue'
import SubTitle from '@/components/comps/SubTitle.vue'
import PUInput from '@/components/lib/Input.vue'

const customStyle = ref({
  color: 'rgb(255, 125, 0)',
  borderColor:'rgb(255, 125, 0)'
})

</script>

<style scoped>


.sub-content {
  background: #fff;
  padding: 10px 12px;
  > * {
    margin-bottom: 15px;
    margin-right: 5px;
  }
}

</style>
