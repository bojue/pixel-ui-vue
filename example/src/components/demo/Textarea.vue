<template>
  <SubTitle text="默认"/>
  <div class="sub-content">
    <PUTextarea placeholder="默认" text="默认内容"></PUTextarea>
  </div>
  <SubTitle text="统计字数"/>
  <div class="sub-content">
    <PUTextarea placeholder="统计字数（默认）" wordCount></PUTextarea>
  </div>
  <SubTitle text="自定义行数"/>
  <div class="sub-content">
    <PUTextarea placeholder="行数：3行" rows="3"></PUTextarea>
  </div>
  <SubTitle text="圆角"/>
  <div class="sub-content">
    <PUTextarea placeholder="圆角" rounded></PUTextarea>
  </div>
  <SubTitle text="底部边框"/>
  <div class="sub-content">
    <PUTextarea placeholder="底部边框" border="bottom"></PUTextarea>
  </div>
  <SubTitle text="无边框"/>
  <div class="sub-content">
    <PUTextarea placeholder="无边框" border="none"></PUTextarea>
  </div>
  <SubTitle text="状态"/>
  <div class="sub-content">
    <PUTextarea placeholder="禁止" value="测试禁止功能" disabled></PUTextarea>
    <PUTextarea placeholder="只读" value="测试只读功能" readonly></PUTextarea>
  </div>
</template>
<script setup>
import { ref, computed } from 'vue'
import SubTitle from '@/components/comps/SubTitle.vue'
import PUTextarea from '@/components/lib/Textarea.vue'

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
