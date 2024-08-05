<template>
  <button :class="classes" :disabled="disabled || loading" :style="compStyles" @click="$emit('click')">
    <!-- <span class="icon"> <img src="https://fastly.jsdelivr.net/npm/@vant/assets/icon-demo.png" alt=""></span> -->
    <!-- <span class="loading">
    <svg viewBox="0 0 14 14"><defs><linearGradient id="grad1-inner-0" x1="0%" y1="0%" x2="100%" y2="0%"><stop offset="0%" class="loading-circle-middle stop-color-with-config"></stop><stop offset="100%" class="loading-circle-start stop-color-with-config"></stop></linearGradient><linearGradient id="grad2-inner-0" x1="0%" y1="0%" x2="100%" y2="0%"><stop offset="0%" class="loading-circle-middle stop-color-with-config"></stop><stop offset="100%" class="loading-circle-end stop-color-with-config"></stop></linearGradient></defs><circle cx="7" cy="7" r="6" stroke="url(#grad1-inner-0)" stroke-width="2" stroke-dasharray="18.84955592153876" stroke-dashoffset="18.84955592153876" fill="none"></circle><circle cx="7" cy="7" r="6" stroke="url(#grad2-inner-0)" stroke-width="2" stroke-dasharray="18.84955592153876" fill="none"></circle><circle cx="13" cy="7" r="1" class="loading-circle-filleted fill-color-with-config"></circle></svg>
  </span> -->
    <!-- <span class="">{{ text }}</span> -->
    <span class="icon">+</span>
  </button>
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
  width: String
})

const {
  type,
  plain,
  color,
  size,
} = props
const classes = computed(() => ['pu-btn', `pu-btn-${type}`, {
  'pu-btn-plain': plain
}])

const compStyles = computed(() => {
  const _size = getFabSize(size)

  const style = {
    background: color,
    width: _size,
    height: _size
  }
  console.log('_size', _size, style, 'size', size)
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
}

.pu-btn-default {
  background: #fff;
  border-color: #d9d9d9;
  color: rgba(0, 0, 0, 0.88);

  &.pu-btn-plain {
    background: #fff;
    color: rgba(0, 0, 0, 0.88);
  }
}

.pu-btn-primary {
  background: #165DFF;
  border-color: #165DFF;

  &.pu-btn-plain {
    background: #fff;
    color: #165DFF;
  }
}

.pu-btn-success {
  background: #07c160;
  border-color: #07c160;

  &.pu-btn-plain {
    background: #ffffff;
    color: #07c160;
  }

}

.pu-btn-warning {
  background: rgb(255, 125, 0);
  border-color: rgb(255, 125, 0);

  &.pu-btn-plain {
    background: #ffffff;
    color: rgb(255, 125, 0);
  }
}

.pu-btn-danger {
  background: rgb(245, 63, 63);
  border-color: rgb(245, 63, 63);

  &.pu-btn-plain {
    background: #ffffff;
    color: rgb(245, 63, 63);
  }
}
</style>
