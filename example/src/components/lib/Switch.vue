<template>
    <label class="switch"  :class="parentClasses" :style="containerStyle">
      <input type="checkbox" :checked="checkedValue" @input="inputChange($event)">
      <div :class="classes" :style="switchStyle">
        <span v-if="text?.on" class="text" :class="{right: !checkedValue, left: checkedValue}">{{ !checkedValue ? text.on : text.off }}</span>
      </div>
    </label>
</template>
<script lang="ts" setup>
import { ref, computed } from 'vue'

const props = defineProps({
  disabled: Boolean,
  round: Boolean,
  rightAngle: Boolean,
  checked: {
    type: Boolean,
    default: false,
  },
  size: {
    type: String,
    default: 'default'
  },
  activeColor: {
    type: String,
    default: '#165DFF'
  }, 
  inactiveColor: {
    type: String,
    default: '#e5e6eb'
  },
  text: {
    type: Object,
  }
  
})

const {
  round,
  size,
  text,
  checked,
  rightAngle,
  activeColor,
  inactiveColor,
  disabled
} = props
const inActiveTextColor = '#4e5969'
const activeTextColor = '#fff'
const checkedValue = ref(checked)

const parentClasses = computed(() => [
  'pu-form-item-container',
  {
    'pu-switch-size-default': size === 'default',
    'pu-switch-size-small': size === 'small',
  }
])

const classes = computed(() => [
  'pu-switch',
  'slider',
  'pu-switch-round',
  { 
    'pu-switch-disabled': disabled,
    'pu-switch-rightAngle': rightAngle,
  }])

const containerStyle = computed(() => {
  const {
    height,
    width,
    padding 
  } = buttonSizeConfig(size)
  const style = {
    '--switch-size-width': width + 'px',
    '--switch-size-height': height + 'px',
    '--switch-slider-padding': padding + 'px',
    '--switch-slider-size': ((height - padding * 2)) + 'px',
    '--switch-slider-transform-x': (width - (height - padding)- padding) + 'px'
  }
  return style
})

const compStyles = computed(() => {
  const style = {

  }
  return style
})


const buttonSizeConfig = (state) => {
  const sizeMap = {
    default: {
      height: 34,
      width: 62,
      padding: 3,
    },
    small: {
      height: 28,
      width: 50,
      padding: 3,
    }
  }
  const customStyle = {}
  if(!sizeMap[state] && parseInt(state)) {
    customStyle[state] = {
      height: parseInt(state),
      width: parseInt(state) * 2 - 3*2,
      padding: 3,
    }
  }
  return sizeMap[state] || customStyle[state] || sizeMap['default']
}

const switchStyle = computed(() => {
  const style = {
    '--active-color': activeColor,
    '--inactive-color': inactiveColor,
    '--text-active-color': activeTextColor,
    '--text-inactive-color': inActiveTextColor
  }
return style
})

const inputChange = (event) => {
  const value = event.target.checked
  checkedValue.value = value
}


</script>

<style lang="scss" scoped>
.pu-switch {
  color: rgb(48, 49, 51);
  font-size: 16px;
  padding: 2px 4px;
}

.pu-switch-disabled {
  opacity: 0.5;
}

.switch {
  position: relative;
  display: inline-block;
  width: var(--switch-size-width);
  height: var(--switch-size-height);
}

.switch input {
  display: none;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: var(--inactive-color);
  -webkit-transition: .4s;
  transition: .4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: var(--switch-slider-size);
  width: var(--switch-slider-size);
  left: var(--switch-slider-padding);
  bottom: var(--switch-slider-padding);
  background-color: white;
  -webkit-transition: .4s;
  transition: .4s;
}

input:checked +.slider {
  background-color: var(--active-color);
}

input:focus+.slider {
  box-shadow: 0 0 1px var(--active-color);
}

input:checked+.slider:before {
  transform: translateX(var(--switch-slider-transform-x)); 
}

.slider {
  &.pu-switch-round {
    border-radius: 99999px;
    &:before {
      border-radius: 50%;
    }
  }
  &.pu-switch-rightAngle {
    border-radius: 0;
    &:before {
      border-radius: 0;
    }
  }
}

.text {
  height: 10px;
  font-size: 14px;
  line-height: 1;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  &.left {
    left: 8px;
    color: var(--text-active-color);
  }
  &.right {
    right: 8px;
    color: var(--text-inactive-color);
  }
}

</style>
