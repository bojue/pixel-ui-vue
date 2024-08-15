<template>
  <view  :class="parentClasses" >
    <input 
      :class="classes"
      :type="type" 
      :style="compStyles"  
      :readonly="readonly"
      :disabled="disabled"
      :maxLength="maxLength"
      :placeholder="placeholder"
      :value="value" 
      @input=handInput($event)>
      <div class="word-count" v-if="wordCount || wordCountOnly">
        <span class="word-count-value">0</span>
        <span class="word-count-symbol" v-if="!wordCountOnly">/</span>
        <span class="word-count-max" v-if="!wordCountOnly">{{ total }}</span>
      </div>
  </view>
</template>
<script lang="ts" setup>
import { ref, computed } from 'vue'

const props = defineProps({
  text:{
    type: String,
    required: true
  },
  placeholder: String, 
  border: String, 
  type: {
    type: String,
    default: 'text'
  },
  total: {
    type: Number,
    default: 10,
  },
  value: String,
  textAlign: String,
  maxLength: Number,
  wordCount: Boolean,
  rounded: Boolean, 
  circle: Boolean,
  disabled: Boolean,
  readonly: Boolean,
  wordCountOnly: Boolean,

})

const { 
  placeholder,
  textAlign,
  disabled,
  rounded,
  readonly,
  wordCountOnly,
  circle,
  value,
  type,
  border,
  wordCount,
  maxLength,
  total
} = props

let word = ref()
const handInput = (event) => {
  word.value = event.target.value
  const countContainerDom = event.currentTarget.nextElementSibling
  const countDom = countContainerDom?.getElementsByClassName('word-count-value')?.[0]
  if(countDom) {
    const len = word.value?.length
    countDom.innerHTML = len
    const hasErrorClass = countContainerDom?.classList?.contains('error')
    if(len > total && !hasErrorClass && !wordCountOnly) {
      countContainerDom.classList?.add('error')
    } else if(len <= total && hasErrorClass && !wordCountOnly){
      countContainerDom.classList?.remove('error')
    }
  }
}

const parentClasses = computed(() => [
  'pu-form-item-container',
  {
    'pu-input-border-rounded': rounded,
    'pu-input-border-circle': circle,
    'no-border': border === 'none',
    'border-bottom': border === 'bottom'
  }
])

const classes = computed(() => [
    'pu-input',
    {
      'pu-input-border-rounded': rounded,
      'pu-input-border-circle': circle,
    }

])

const compStyles = computed(() => {
  const style = {
    textAlign
  }
  return style
})
</script>

<style lang="scss" scoped>
input {
  outline-style: none;
  :disabled{
    background: rgba(120, 120, 128, 0.1);
    cursor: not-allowed;
    outline: none;
  }
  :focus {
    border-color: #66afe9;
    outline: 0;
    -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075),0 0 8px rgba(102,175,233,.6);
    box-shadow: inset 0 1px 1px rgba(0,0,0,.075),0 0 8px rgba(102,175,233,.6)
  }
}

.pu-form-item-container {
  display: flex;
  width: 100%;
  position: relative;
  border: 1px solid #e5e6eb;
}
.pu-input {
  position: relative;
  font-size: 14px;
  padding: 8px 16px;
  height: 24px;
  line-height: 24px;
  width: -webkit-fill-available;
  color: #1d2129;
  display: flex;
  border:none;
  &::placeholder {
    color: #aaa;
  }
}


.pu-input-border-rounded {
  border-radius: 6px;
}

.pu-input-border-circle {
  border-radius: 9999px;
}

.no-border {
  border: none;
}

.border-bottom {
  border: none;
  border-bottom: 1px solid #e5e6eb;
}

.word-count {
  color: #86909c;
  font-size: 12px;
  right: 10px;
  bottom: 10px;
  padding: 4px;
  line-height: 32px;
}

.error {
  color: #F53F3F;
}

</style>



