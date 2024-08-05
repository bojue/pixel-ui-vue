<template>
  <SubTitle text="按照类型"/>
  <div class="sub-content">
    <PUFab type="primary"></PUFab>
    <PUFab type="primary" size="40px"></PUFab>
    <PUFab type="success"></PUFab>
    <PUFab type="warning"></PUFab>
    <PUFab type="danger"></PUFab>
  </div>
  <SubTitle text="线框按钮"/>
  <div class="sub-content">
    <PUFab type="primary" plain></PUFab>
    <PUFab type="success" plain></PUFab>
    <PUFab type="warning" plain></PUFab>
    <PUFab type="danger"  plain></PUFab>
  </div>
  <SubTitle text="含自定义图标"/>
  <div class="sub-content">
    <PUFab type="primary"></PUFab>
  </div>
  <SubTitle text="按钮大小"/>
  <div class="sub-content">
    <PUFab type="primary" size="extraLarge"></PUFab>
    <PUFab type="danger"  size="large"></PUFab>
    <PUFab type="warning" size="default"></PUFab>
    <PUFab type="success" size="middle"></PUFab>
  </div>
  <SubTitle text="自定义颜色"/>
  <div class="sub-content">
    <PUFab color="#7232dd"></PUFab>
    <PUFab color="#7232dd" plain></PUFab>
    <PUFab color="linear-gradient(red, yellow, blue, orange)"></PUFab>
  </div>
  <SubTitle text="自定义大小"/>
  <div class="sub-content">
    <PUFab type="primary" size="80px"></PUFab>
  </div>
</template>
<script setup>
import { ref, computed } from 'vue'
import SubTitle from '@/components/comps/SubTitle.vue'
import PUFab from '@/components/lib/Fab.vue'

const getFontSize = (size) => {
  const data = {
    large: '16px',
    default: '14px',
    small: '12px',
    mini: '10px'
  }

  return data[size] || size
}

</script>

<style scoped>


.sub-content {
padding: 10px 20px;
background: #fff;
/* align-items: flex-end;
display: flex; */
> * {
  margin-right: 15px;
  margin-bottom: 15px;
  }
}

</style>
