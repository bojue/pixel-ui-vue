<template>
  <SubTitle text="按照类型"/>
  <div class="sub-content">
    <PUFab ></PUFab>
    <PUFab plain></PUFab>
  </div>
  <SubTitle text="按钮大小"/>
  <div class="sub-content">
    <PUFab size="extraLarge"></PUFab>
  </div>
  <SubTitle text="自定义颜色"/>
  <div class="sub-content">
    <PUFab color="#7232dd"></PUFab>
    <PUFab color="#7232dd" plain></PUFab>
    <PUFab color="linear-gradient(to bottom left, cyan 50%, palegoldenrod 50%);" noBorder></PUFab>
  </div>
  <SubTitle text="自定义大小"/>
  <div class="sub-content">
    <PUFab size="80px"></PUFab>
  </div>
</template>
<script setup>
import { ref, computed } from 'vue'
import SubTitle from '@/components/comps/SubTitle.vue'
import PUFab from '@/components/lib/Fab.vue'
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
