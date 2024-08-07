<template>
    <button :class="classes" :disabled="disabled || loading" :style="compStyles" @click="$emit('click')">
    <!-- <span class="icon"> <img src="https://fastly.jsdelivr.net/npm/@vant/assets/icon-demo.png" alt=""></span> -->
    <!-- <span class="loading">
      <svg viewBox="0 0 14 14"><defs><linearGradient id="grad1-inner-0" x1="0%" y1="0%" x2="100%" y2="0%"><stop offset="0%" class="loading-circle-middle stop-color-with-config"></stop><stop offset="100%" class="loading-circle-start stop-color-with-config"></stop></linearGradient><linearGradient id="grad2-inner-0" x1="0%" y1="0%" x2="100%" y2="0%"><stop offset="0%" class="loading-circle-middle stop-color-with-config"></stop><stop offset="100%" class="loading-circle-end stop-color-with-config"></stop></linearGradient></defs><circle cx="7" cy="7" r="6" stroke="url(#grad1-inner-0)" stroke-width="2" stroke-dasharray="18.84955592153876" stroke-dashoffset="18.84955592153876" fill="none"></circle><circle cx="7" cy="7" r="6" stroke="url(#grad2-inner-0)" stroke-width="2" stroke-dasharray="18.84955592153876" fill="none"></circle><circle cx="13" cy="7" r="1" class="loading-circle-filleted fill-color-with-config"></circle></svg>
    </span> -->
      <span class="">{{ text }}</span>
    </button>
</template>
<script lang="ts" setup>
import { ref, computed } from 'vue'

const props = defineProps({
  disabled:{
    type: Boolean,
    default: false
  },
  text:{
    type: String,
    default: 'Primary'
  },
  type:{
    type: Boolean,
    default: 'default'
  },
  plain:{
    type: Boolean,
    default: false
  },
  fillet: {
    type: Boolean,
    default: false
  },
  rounded: {
    type: Boolean,
    default: false
  },
  color: String,
  shape: String,
  size: {
    type: String,
    default: '14px'
  },
  width: String,
  block: Boolean,
  loading: Boolean
})

const {
  type,
  disabled,
  text,
  plain,
  fillet,
  rounded,
  color,
  size,
  width,
  block,
  loading
} = props
const classes = computed(() => ['pu-btn', `pu-btn-${type}`, `pu-btn-size-${size}`, `pu-btn-width-${width}`, {
  'pu-btn-plain': plain,
  'pu-btn-disabled': disabled,
  'pu-btn-fillet': fillet,
  'pu-btn-rounded': rounded,
  'pu-btn-block': block,
  'pu-btn-loading': loading
}])

const compStyles = computed(() => {
  const hasColor = color
  if(hasColor) {
    switch(plain) {
    case true:
      return {
        color: color,
        borderColor: color,
      }
    default:
      return {
        color: '#ffffff',
        background: color,
        borderColor: color
      }
  }}
})

</script>

<style scoped>

.pu-btn {
  cursor: pointer;
  border-radius: 0;
  color: #fff;
  font-size: 16px;
  font-weight: 400;
  border-radius: 0px;
  height: 40px;
  padding: 4px 15px;
  border: 1px solid #d9d9d9;
}

.pu-btn-disabled {
  opacity: 0.5;
  cursor: not-allowedr;
}

.pu-btn-loading {
  opacity: 0.65;
  cursor: default;
}


.pu-btn-fillet {
  border-radius: 6px;
}

.pu-btn-rounded {
  border-radius: 40px;
}

.pu-btn-block {
  display: block;
  width: 100%;
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
  background:#07c160;
  border-color: #07c160;

  &.pu-btn-plain {
    background: #ffffff;
    color: #07c160;
  }

}
.pu-btn-warning {
  background: rgb(255, 125, 0);
  border-color:rgb(255, 125, 0);
  
  &.pu-btn-plain{
    background:#ffffff;
    color:rgb(255, 125, 0);
  }
}
.pu-btn-error {
  background: rgb(245, 63, 63);
  border-color: rgb(245, 63, 63);
  &.pu-btn-plain{
    background: #ffffff;
    color: rgb(245, 63, 63);
  }
}

.pu-btn-size-large {
  padding: 6.5px 15px;
  height: 50px;
  font-size: 16px;
  width: 100%;
}

.pu-btn-size-default {
  padding: 4px 15px;
  height: 40px;
  font-size: 16px;
}

.pu-btn-size-small {
  padding: 0px 7px;
  height: 32px;
  font-size: 14px;
}

.pu-btn-size-mini {
  padding: 0px 7px;
  height: 26px;
  font-size: 12px;
}

.pu-btn-width-full {
  width: 100%;
}

.pu-btn-width-half {
  width: 50%;
}

.pu-btn-width-quird {
  width: 33.33%;
}

.pu-btn-loading {
  opacity: 0.65;
  cursor: default;
}

.pu-btn-auxiliary {
  color: #165DFF;
  background: #E8F3FF;
  border-color: #E8F3FF;
}

.loading {
  padding: 4px;
  svg {
    vertical-align: middle;
    width: 16px;
    height: 16px;
  }
}

.icon {
  margin: 0 5px;
  width: 20px;
  img {
    vertical-align: middle;
  }
}
</style>
