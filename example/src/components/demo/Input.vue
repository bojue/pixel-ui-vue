<template>
  <SubTitle text="默认"/>
  <div class="sub-content">
    <PUInput placeholder="默认" text="默认内容"></PUInput>
  </div>
  <SubTitle text="自定义类型"/>
  <div class="sub-content">
    <PUInput type="text" placeholder="默认文本"></PUInput>
    <PUInput type="password" placeholder="密码"></PUInput>
    <PUInput type="number" placeholder="数字"></PUInput>
  </div>
  <SubTitle text="边角"/>
  <div class="sub-content">
    <PUInput placeholder="默认（直角）"></PUInput>
    <PUInput placeholder="圆角" rounded></PUInput>
    <PUInput placeholder="圆形" circle></PUInput>
  </div>

  <SubTitle text="底部边框"/>
  <div class="sub-content">
    <PUInput placeholder="底部边框" border="bottom"></PUInput>
  </div>
  <SubTitle text="无边框"/>
  <div class="sub-content">
    <PUInput placeholder="无边框" border="none"></PUInput>
  </div>
  <SubTitle text="可清空内容"/>
  <div class="sub-content">
    <PUInput></PUInput>
  </div>
  <SubTitle text="统计字数"/>
  <div class="sub-content">
    <PUInput placeholder="统计字数（默认）" wordCount></PUInput>
    <PUInput placeholder="自定义长度：12" wordCount total="12"></PUInput>
    <PUInput placeholder="仅统计字数" wordCountOnly></PUInput>
  </div>
  <SubTitle text="最大长度"/>
  <div class="sub-content">
    <PUInput placeholder="最大长度(maxLength=20)" maxLength="20"></PUInput>
  </div>
  <SubTitle text="状态"/>
  <div class="sub-content">
    <PUInput placeholder="禁止" value="测试禁止功能" disabled></PUInput>
    <PUInput placeholder="只读" value="测试只读功能" readonly></PUInput>
  </div>
  <SubTitle text="文字位置"/>
  <div class="sub-content">
    <PUInput placeholder="左侧" value="左侧" text-align="left"></PUInput>
    <PUInput placeholder="中间" value="中间" text-align="center"></PUInput>
    <PUInput placeholder="右侧" value="右侧" text-align="right"></PUInput>
  </div>
  <!-- <SubTitle text="前后插槽"/>
  <div class="sub-content">
    <PUInput placeholder="前插槽"></PUInput>
    <PUInput placeholder="后插槽"></PUInput>
  </div> -->
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
    margin-bottom: 8px;
    margin-right: 5px;
  }
}

</style>
