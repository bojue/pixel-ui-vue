
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
      <PUTagDemo v-if="currType == 'tag'" />
    </div>
  </div>
</template>
<script setup>
import { ref } from 'vue'
import PUDividerDemo from '@/components/demo/Divider.vue'
import PUButtonDemo from '@/components/demo/Button.vue'
import PUTextDemo from '@/components/demo/Text.vue'
import PUFabDemo from '@/components/demo/Fab.vue'
import PUTagDemo from '@/components/demo/Tag.vue'

defineProps({
  msg: String,
})

const currType = ref('tag')
const list = ref([{
  name: '按钮(Button)',
  type: 'button'
}, {
  name: '文本(Text)',
  type: 'text'
},{
  name: '分割线(Divider)',
  type: 'divider'
}, {
  name: '浮选按钮(Fab)',
  type: 'fab'
}, {
  name: '标签(Tag)',
  type: 'tag'
}])
</script>


<style lang="scss" scoped>

.components {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 580px;
  display: flex;
  flex-direction: row;

  .comp-list {
    width: 140px;
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
