<template>
  <view :class="parentClasses" >
    <textarea 
      :class="classes"
      :type="type" 
      :style="compStyles"  
      :readonly="readonly"
      :disabled="disabled"
      :maxLength="maxLength"
      :placeholder="placeholder"
      :value="value" 
      @input=handInput($event) 
      >
      </textarea>
      <span class="word-count" v-if="wordCount">
        <span class="word-count-value">0</span>
        <span class="word-count-symbol">/</span>
        <span class="word-count-max">{{ total }}</span>
      </span>
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
    default: 140,
  },
  value: String,
  maxLength: Number,
  rows: {
    type: Number,
    default: 2,
  },
  wordCount: Boolean,
  rounded: Boolean, 
  circle: Boolean,
  disabled: Boolean,
  readonly: Boolean,
  wordCountOnly: Boolean,

})

const { 
  placeholder,
  disabled,
  rounded,
  readonly,
  rows,
  value,
  border,
  wordCount,
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
    if(len > total && !hasErrorClass) {
      countContainerDom.classList?.add('error')
    } else if(len <= total && hasErrorClass){
      countContainerDom.classList?.remove('error')
    }
  }
}

const parentClasses = computed(() => [
  'pu-form-item-container',
])

const classes = computed(() => [
  'pu-textarea',
  {
    'pu-textarea-border-rounded': rounded,
    'no-border': border === 'none',
    'border-bottom': border === 'bottom'
  }

])

const compStyles = computed(() => {
  const style = {
  }
  return style
})
</script>

<style lang="scss" scoped>
textarea {
  outline-style: none;
  resize: none;
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
  width: 100%;
  position: relative;
  display: inline-block;
}
.pu-textarea {
  font-size: 14px;
  padding: 8px 16px;
  line-height: 24px;
  width: -webkit-fill-available;
  color: #1d2129;
  border: 1px solid #e5e6eb;
  &::placeholder {
    color: #aaa;
  }
}


.pu-textarea-border-rounded {
  border-radius: 6px;
}

.pu-textarea-border-circle {
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
  right: 8px;
  left: auto;
  bottom: 5px;
  line-height: 32px;
  position: absolute;
}

.error {
  color: #F53F3F;
}

</style>



