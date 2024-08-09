<template>
  <view class="pu-form-item-container" :class="parentClasses" :style="compStyles">
    <input type="text" :class="classes" :placeholder="placeholder" >
  </view>
</template>
<script lang="ts" setup>
import { ref, computed } from 'vue'

const props = defineProps({
  text:{
    type: String,
    required: true
  },
  placeholder: String 


})

const { 
  placeholder
} = props

const parentClasses = computed(() => {

})

const classes = computed(() => [
    'pu-input'

])

const compStyles = computed(() => {
  const style = {

  }
  return style
})
</script>

<style scoped>
.pu-form-item-container {
  display: flex;
  width: 100%;
}
.pu-input {
  font-size: 14px;
  padding: 5px 10px;
  height: 24px;
  line-height: 24px;
  width: 100%;
  color: rgb(48, 49, 51);
  border: 1px solid #eaf0fb;
  display: flex;
}




</style>



