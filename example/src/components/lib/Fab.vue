<template>
  <div :class="classes" :disabled="disabled || loading" :style="compStyles" @click="$emit('click')">
    <span class="icon">+</span>
  </div>
</template>
<script lang="ts" setup>
import { ref, computed } from 'vue'

const props = defineProps({
  disabled: {
    type: Boolean,
    default: false
  },
  type: {
    type: Boolean,
    default: 'default'
  },
  plain: {
    type: Boolean,
    default: false
  },
  size: String,
  color: String,
  width: String,
  noBorder: Boolean
})

const {
  type,
  plain,
  color,
  size,
  noBorder
} = props
const classes = computed(() => ['pu-btn', `pu-btn-${type}`, {
  'pu-btn-plain': plain,
  'pu-btn-no-border': noBorder
}])

const compStyles = computed(() => {
  const _size = getFabSize(size)

  const style = {
    background: color,
    width: _size,
    height: _size
  }
  return style
})


const getFabSize = (size) => {
  const data = {
    extraLarge: '72px',
    large: '60px',
    default: '48px',
    middle: '40px'
  }

  return data[size] || size || data['default']
}


</script>

<style scoped>
.pu-btn {
  cursor: pointer;
  color: #fff;
  border-radius: 0px;
  width: 48px;
  height: 48px;
  font-size: 40px;
  border-radius: 50%;
  border-width: 1px;
  border-style: solid;
  z-index: 10001;

  background: #165DFF;
  border-color: #165DFF;

  &.pu-btn-plain {
    background: #fff;
    color: #165DFF;
  }
}

.pu-btn-no-border {
  border: none;
}

</style>
