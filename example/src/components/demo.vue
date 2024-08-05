
<template>
  <h2>组件库</h2>
  <div class="components">
    <div class="comp-list">
      <div class="comp-item" v-for="item of list" @click="currType = item.type" :class="{active: currType === item.type}">
        {{ item.name }}
      </div>
    </div>
    <div class="pixel-mobile">
      <PUDividerDemo v-if="currType === 'divider'" />
      <PUButtonDemo v-if="currType === 'button'"/>
      <PUTextDemo v-if="currType === 'text'"/>
      <PUFabDemo v-if="currType == 'fab'" />
    </div>
  </div>
</template>
<script setup>
import { ref } from 'vue'
import PUDividerDemo from '@/components/demo/Divider.vue'
import PUButtonDemo from '@/components/demo/Button.vue'
import PUTextDemo from '@/components/demo/Text.vue'
import PUFabDemo from '@/components/demo/Fab.vue'

defineProps({
  msg: String,
})

const currType = ref('fab')
const list = ref([{
  name: '按钮',
  type: 'button'
}, {
  name: '文本',
  type: 'text'
},{
  name: '分割线',
  type: 'divider'
}, {
  name: '浮选按钮',
  type: 'fab'
}])
</script>


<style lang="scss" scoped>

.components {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 500px;
  display: flex;
  flex-direction: row;

  .comp-list {
    width: 90px;
    margin: 0 10px;
  }

  .comp-item {
    width: 100%;
    height: 32px;
    line-height: 32px;
    color: #fff;
    border-radius: 5px;
    margin-bottom: 10px;
    margin-right: 10px;
    text-align: center;
    border: 1px solid #d9d9d9;
    color: rgba(0, 0, 0, 0.88);

    &.active {
      border: 1px solid #165DFF;
      background: #165DFF;
      color: #FFF;
    }
  }
}


.pixel-mobile {
  width: 360px;
  height: 1640px;
  border: 1px solid #e5e6eb;
  background: #F7F8FA;
  border-radius: 6px;
  box-shadow: 0px 0px 24px rgba(0, 0, 0, 0.07);
}

</style>
