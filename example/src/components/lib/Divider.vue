<template>
  <div class="pu-divider" :class="classes" :style="compStyles">
    {{text}}
  </div>
</template>
<script lang="ts" setup>
import { ref, computed } from 'vue'

const props = defineProps({
  text:{
    type: String,
    default: ''
  },
  type: {
    type: String,
    default: 'solid'
  },
  plain: Boolean,
  bold: Boolean,
  thin: Boolean,
  align: String,
  color: String,
  contentColor: String,
  borderColor: String,
  borderStyle: String, 
  background: String,
  size: String,
  width: {
    type: String,
    default: '100%'
  },
  height: String
})

const {
  text,
  type,
  bold,
  thin,
  align,
  size,
  contentColor,
  color,
  borderColor,
  borderStyle,
  background,
  width,
  height
} = props
const classes = computed(() => [
  'pu-divider', 
  `pu-divider-style-${type}`,
  align && `pu-divider-align-${align}`, 
  {
    'pu-divider-after': !!text,
    'pu-divider-bold': bold,
    'pu-divider-thin': thin
  }])

const compStyles = computed(() => {
  const _fontSize = getFontSize(size)
  const data = {
    color: contentColor || color,
    borderColor: borderColor || color,
    borderStyle: background ? 'none': borderStyle,
    background,
    fontSize: _fontSize,
    height,
    '--max-width': width
  }
  return data
})

const getFontSize = (size) => {
  const data = {
    large: '18px',
    default: '16px',
    small: '14px',
    mini: '12px'
  }

  return data[size] || size
}



</script>

<style lang="scss" scoped>

.pu-divider {
  display: -webkit-box;
  display: -webkit-flex;
  font-size: 16px;
  display: flex;
  -webkit-box-align: center;
  -webkit-align-items: center;
  align-items: center;
  -webkit-box-pack: center;
  -webkit-justify-content: center;
  justify-content: center;
  padding: 0.32rem 0;
  border-color: #e5e6eb;
  border-width: 0;
  border-style: solid;
  color: #4e5969;

  &::before, &.pu-divider-after::after {
    content: '';
    transform: scaleY(0.9);
    -webkit-box-flex: 1;
    -webkit-flex-grow: 1;
    flex-grow: 1;
    -webkit-flex-shrink: 1;
    flex-shrink: 1;
    -webkit-flex-basis: inherit;
    flex-basis: inherit;
    border-width: 0;
    border-color: inherit;
    border-style: inherit;
    border-top-width: 1PX;
    border-top-width: 1px;
    max-width: var(--max-width);
  }
}

.pu-divider-after {
  &::before {
    margin-right: 15px;
  } 
  &::after {
    margin-left: 15px;
  }
}

.pu-divider-style-dashed {
  border-style: dashed;
}

.pu-divider-style-dotted {
  border-style: dotted;
}

.pu-divider-style-strip {
  border-style: none;
  background: #e5e6eb;
}

.pu-divider-align-right {
  &::after {
    max-width: 15%;
  }
}

.pu-divider-align-left {
  &::before {
    max-width: 15%;
  }
}

.pu-divider-bold {
  &::before {
    transform: scaleY(1.5);
  } 
  &.pu-divider-after::after{
    transform: scaleY(1.5);
    
  }
}

.pu-divider-thin {
  &::before {
    transform: scaleY(0.5);
  } 
  &.pu-divider-after::after{
    transform: scaleY(0.5);
    
  }
}


</style>
