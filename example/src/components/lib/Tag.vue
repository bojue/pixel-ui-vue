<template>
    <span :class="classes" :disabled="disabled || loading" :style="compStyles" @click="$emit('click')">
      <span class="">{{ text }}</span>
    </span>
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
  rounded: {
    type: Boolean,
    default: false
  },
  color: String,
  shape: String,
  width: String,
  size: String,
  light: Boolean,
  fillet: Boolean
})

const {
  type,
  text,
  plain,
  fillet,
  rounded,
  color,
  size,
  light,
  width,
} = props
const classes = computed(() => ['pu-tag', `pu-tag-${type}`, `pu-tag-size-${size}`, {
  'pu-tag-plain': plain,
  'pu-tag-rounded': rounded,
  'pu-tag-light': light,
  'pu-tag-fillet': fillet,
  'pu-tag-max-width': !!width
}])

const compStyles = computed(() => {
  const _colorConfig = getColorStyle(color)
  const style = {
    ..._colorConfig,
    '--max-width': width,
  }
  return style
})

const getColorStyle = (color) => {
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
}

</script>

<style scoped>

.pu-tag {
  cursor: pointer;
  border-radius: 0;
  color: #fff;
  font-size: 14px;
  border-radius: 0px;
  padding: 0px 8px;
  height: 24px;
  line-height: 24px;
  border: 1px solid #d9d9d9;
  display: inline-block;
}

.pu-tag-rounded {
  border-radius: 40px;
}

.pu-tag-default {
  background: #fff;
  border-color: #d9d9d9;
  color: rgba(0, 0, 0, 0.88);

  &.pu-tag-plain {
    background: #fff;
    color: rgba(0, 0, 0, 0.88);
  }
  &.pu-tag-light {
    color: rgba(0, 0, 0, 0.88);
    background: #f3f3f3;
    border-color: #f3f3f3;
    &.pu-tag-plain {
      border-color: #d9d9d9;
    }
  }
}
.pu-tag-primary {
  background: #165DFF;
  border-color: #165DFF;

  &.pu-tag-plain {
    background: #fff;
    color: #165DFF;
  }
  &.pu-tag-light {
    color: #165DFF;
    background: #E8F3FF;
    border-color: #E8F3FF;
    &.pu-tag-plain {
      border-color: #165DFF;
    }
  }
}

.pu-tag-success {
  background:#07c160;
  border-color: #07c160;

  &.pu-tag-plain {
    background: #ffffff;
    color: #07c160;
  }
  &.pu-tag-light {
    color: #07c160;
    background: #e3f9e9;
    border-color: #e3f9e9;
    &.pu-tag-plain {
      border-color: #07c160;
    }
  }

}
.pu-tag-warning {
  background: rgb(255, 125, 0);
  border-color:rgb(255, 125, 0);
  
  &.pu-tag-plain{
    background:#ffffff;
    color:rgb(255, 125, 0);
  }
  &.pu-tag-light {
    color:rgb(255, 125, 0);
    background: #fff1e9;
    border-color: #fff1e9;
    &.pu-tag-plain {
      border-color:rgb(255, 125, 0);
    }
  }
}
.pu-tag-error {
  background: rgb(245, 63, 63);
  border-color: rgb(245, 63, 63);
  &.pu-tag-plain{
    background: #ffffff;
    color: rgb(245, 63, 63);
  }
  &.pu-tag-light {
    color: rgb(245, 63, 63);
    background: #fff0ed;
    border-color: #fff0ed;
    &.pu-tag-plain {
      border-color: rgb(245, 63, 63);
    }
  }
}

.pu-tag-size-large {
  padding: 0px 15px;
  font-size: 14px;
  height: 28px;
  line-height: 28px;
}

.pu-tag-size-default {
  font-size: 14px;
}

.pu-tag-size-small {
  padding: 0px 6px;
  font-size: 12px;
  height: 20px;
  line-height: 20px;
}

.pu-tag-size-mini {
  padding: 0px 4px;
  font-size: 12px;
  height: 18px;
  line-height: 18px;
}

.pu-tag-fillet {
  border-radius: 4px;
}

.pu-tag-max-width {
  width: var(--max-width);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>
