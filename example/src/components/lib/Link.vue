<template>
  <a :class="classes" :href="href" :text="text" :style="compStyles"></a>
</template>
<script lang="ts" setup>
import { ref, computed } from 'vue'

const props = defineProps({
  href: String,
  disabled: Boolean,
  text: String,
  color:String,
  underline: Boolean,
  linkColor: String,
  background: String,
})

const {
  href,
  underline,
  disabled,
  background,
  text,
  color,
  linkColor
} = props

const classes = computed(() => [
  'pu-link', 
  {
    'pu-link-border-bottom-underline': underline,
  }])

const compStyles = computed(() => {
  const style = {
    color,
    background,
    '--text-decoration-color': linkColor
  }
  return style
})


</script>

<style scoped>

.pu-link {
  color: #165DFF;
  font-size: 14px;
  padding: 2px 4px;
  text-decoration: none;
}

.pu-link-border-bottom-underline {
  text-decoration: underline;
  text-decoration-color: var(--text-decoration-color);
}

</style>
