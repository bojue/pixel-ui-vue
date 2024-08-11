<template>
  <h2>组件库</h2>
  <div class="components">
    <div class="comp-classification">
      <div class="classification-item" v-for="item of list">
        <div class="title">{{ item.name }}</div>
        <div class="comp-list">
          <div class="comp-item" v-for="item of item.children" @click="currType = item.type"
            :class="{ active: currType === item.type }">
            {{ item.name }}
          </div>
        </div>
      </div>
    </div>

    <div class="pixel-mobile">
      <PUDividerDemo v-if="currType === 'divider'" />
      <PUButtonDemo v-if="currType === 'button'" />
      <PUTextDemo v-if="currType === 'text'" />
      <PUFabDemo v-if="currType == 'fab'" />
      <PUTagDemo v-if="currType == 'tag'" />
      <PUInputDemo v-if="currType == 'input'" />
      <PUTextareaDemo v-if="currType == 'textarea'" />
      <PUSwitchDemo v-if="currType == 'switch'" />
    </div>
  </div>
</template>
<script setup>
import { ref } from 'vue'
import { data } from './data'
import PUDividerDemo from '@/components/demo/Divider.vue'
import PUButtonDemo from '@/components/demo/Button.vue'
import PUTextDemo from '@/components/demo/Text.vue'
import PUFabDemo from '@/components/demo/Fab.vue'
import PUTagDemo from '@/components/demo/Tag.vue'
import PUInputDemo from '@/components/demo/Input.vue'
import PUTextareaDemo from '@/components/demo/Textarea.vue'
import PUSwitchDemo from '@/components/demo/Switch.vue'

defineProps({
  msg: String,
})

const currType = ref('switch')
const list = ref(data)
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
    word-wrap: normal;
  }

  .classification-item {
    .title {
      opacity: 0.5;
      font-size: 14px;
      height: 40px;
      line-height: 40px;
      font-weight: 500;
      color: rgba(0, 0, 0, 0.58);
    }
  }

  .comp-item {
    width: 100%;
    height: 32px;
    line-height: 32px;
    color: #fff;
    white-space: nowrap;
    text-align: left;
    color: rgba(0, 0, 0, 0.58);
    font-size: 14px;

    &.active {
      color: #165DFF;
      background: aliceblue;
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
