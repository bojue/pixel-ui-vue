<template>
  <div class="pu-form-item-group pu-radio-group">
    <div class="pu-radio-item" v-for="(item, index) of data">
      <input type="radio" :checked="item[valueField] === vMode"  
        :name="valueField"
        :id="item[labelField]">
      <label class="label" :for="item[labelField]" >{{ item[labelField]}}</label>
    </div>
  </div>
</template>
<script lang="ts" setup>
import { ref, computed } from 'vue'

const props = defineProps({
  title: String,
  data: Array,
  vMode: [String, Number, Object],
  labelField: String,
  valueField: String,
})

const {
  title,
  data,
  vMode,
  labelField,
  valueField
} = props

console.log(data, vMode)

const classes = computed(() => [
  'pu-radio',
  {
  }])

const compStyles = computed(() => {
  const style = {

  }
  return style
})


</script>

<style lang="scss" scoped>
.pu-radio-group {
  color: #165DFF;
  font-size: 14px;
  padding: 2px 4px;
  text-decoration: none;
  position: relative;
}

.pu-radio-item {
  margin: 8px 10px;
  color: #323233;
  input[type='radio'] {
    opacity: 0;
    +label {
      position: relative;
      margin-left: 2px;
      top: -2px;
      cursor: pointer;

      &::before {
        content: "";
        position: absolute;
        width: 18px;
        height: 18px;
        border: 1px solid #165DFF;
        left: -26px;
        border-radius: 50%;
      }

      &::after {
        content: "";
        position: absolute;
        left: -29px;
        top: -5px;
        height: 27px;
        width: 27px;
        border-radius: 50%;
        transform: scale(0.5);
      }
    }

    &:checked {
      +label::after {
        background: #165DFF;
      }
    }
    &:focus {
      +label::before {
        box-shadow: 0 0 1px #165DFF;
      }
    }
    &:disabled {
      +label::before {
        border: 1px solid #ddd;
        box-shadow: 0 0 4px #ddd;
      }
    }
  }

}
</style>
