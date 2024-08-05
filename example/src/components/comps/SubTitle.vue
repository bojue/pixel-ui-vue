<template>
  <div class="sub-title">{{text}}</div>
</template>
<script lang="ts" setup>
import { ref, computed } from 'vue'

const props = defineProps({
  text:{
    type: String,
    default: 'Primary'
  },
})

const {
  text
} = props

</script>

<style scoped>

.sub-title {
  font-size: 14px;
  color: #86909c;
  padding: 5px 20px;
  margin: 5px 0;
}

</style>
