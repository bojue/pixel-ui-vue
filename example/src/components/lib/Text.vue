<template>
  <span class="pu-text" :class="classes" :style="compStyles">
    {{ mode ? puModeValue  : text}}
  </span>
</template>
<script lang="ts" setup>
import { ref, computed } from 'vue'

const currencyMap = {
  zh: '¥',
  en: '$',
  enr: '€'
}

const props = defineProps({
  text:{
    type: String,
    required: true,
    default: 'primary'
  },
  type:{
    type: String,
    default: 'default'
  },
  block: Boolean,
  width: String,
  color: String,
  size: String,
  mode: String,
  href: String,
  borderBottom: Boolean,
  borderColor: String,
  background: String,
  currency: String,
  lines: String,
  overflow: String,
  del: Boolean,
  disabled: Boolean,
  underline: Boolean,
  overline: Boolean,
  readonly: Boolean,
})

const {
  type,
  text,
  mode,
  color,
  size,
  width,
  borderBottom,
  borderColor,
  href,
  block,
  overflow,
  lines,
  currency,
  background,
  underline,
  del,
  overline,
  disabled,
  readonly
} = props
const classes = computed(() => [
  'pu-text', 
  `pu-text-${type}`, 
  `pu-text-mode-${mode}`, 
  `pu-text-overflow-${overflow}`,
  `pu-text-decoration-${undefined}`,
  {
    'pu-border-bottom': borderBottom,
    'pu-text-block': block,
    'pu-text-overflow': !!overflow,
    'pu-text-delete': del,
    'pu-text-disabled': disabled,
    'pu-text-underline': underline,
    'pu-text-overline': overline,
    'pu-text-readonly': readonly
  }])

const compStyles = computed(() => {
  const _bgColor = getBorderColor()
  const _fontSize = getFontSize(size)
  const style = {
    '--border-color': _bgColor,
    '--webkit-line-clamp': lines,
    border: !_bgColor && 'none',
    color,
    fontSize: _fontSize,
    background
  }
  return style
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

const puModeValue = computed(() => {
  switch(mode) {
    case 'phone':
      return desensitizePhoneNumber(text)
    case 'name':
      return desensitizeName(text)
    case 'price':
      return desensitizePrice(text);
    default:
      return text
  }
})

function getBorderColor() {
  let bdColor 
  const isHref = mode === 'link' && borderBottom
  // const data = {
  //   info: '#909399',
  //   primary: '#165DFF',
  //   success: '#07c160',
  //   warning: 'rgb(255, 125, 0)',
  //   error: 'rgb(245, 63, 63)'
  // }
  if(isHref) {
    bdColor = '#3c9cff'
  }  
  return borderColor || bdColor
}

function desensitizePrice(num) {
  const str = num?.toString()
  if(!str) {
    return str
  }
  const formatted = str.replace(/\B(?=(\d{3})+\b)/g, ',');
  const data = `${currencyMap[currency]} ${formatted}` 
  return data;
}

function desensitizeName(name) {
  const chineseRegex = /[\u4e00-\u9fa5]/g;
  const middleCharRegex = /^([\u4e00-\u9fa5])([\s\S])([\u4e00-\u9fa5])$/;
  if (chineseRegex.test(name) && middleCharRegex.test(name)) {
    return name.replace(middleCharRegex, '$1*$3');
  } else {
    return name;
  }
}

function desensitizePhoneNumber(phoneNumber) {
  if (!/^\d{11}$/.test(phoneNumber)) {
    return '无效的手机号码';
  }
  return phoneNumber.replace(/(\d{3})\d{4}(\d{4})/, '$1****$2');
}

</script>

<style scoped>

.pu-text {
  color: rgb(48, 49, 51);
  font-size: 16px;
  padding: 2px 4px;
}

.pu-text-primary {
  color: #165DFF;
}
.pu-text-success {
  color: #07c160;
}
.pu-text-warning {
  color: rgb(255, 125, 0);
}
.pu-text-error {
  color:rgb(245, 63, 63);
}
.pu-text-info {
  color: #909399;
}

.pu-text-mode-link {
  color: #3c9cff;
  border-bottom: 1px solid var(--border-color)
}
.pu-text-block {
  display: block;
}

.pu-text-overflow {
  display: -webkit-box;
  -webkit-line-clamp: var(--webkit-line-clamp);
  -webkit-box-orient: vertical;
}


.pu-text-overflow-ellipsis {
  overflow: hidden;
}

.pu-text-overflow-scroll {
  overflow: scroll;
  overflow-x:auto;
}

.pu-text-overline {
  text-decoration: overline;
}

.pu-text-delete {
  text-decoration: line-through;
}

.pu-text-underline {
  text-decoration: underline;
}

.pu-text-disabled {
  opacity: 0.5;
}

.pu-text-readonly {
  user-select: none;
}

</style>
