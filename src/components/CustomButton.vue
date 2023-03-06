<template>
  <v-btn
    flat
    :color="color"
    :width="calcWidth"
    :height="calcHeight"
    class="custom-button"
    @click="$emit('click')"
  >
    <span v-if="text" class="custom-button__text">{{ text }}</span>
    <slot v-else />
  </v-btn>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  text: {
    type: String,
  },
  color: {
    type: String,
    default: 'primary',
  },
  // ボタンのサイズを決める基準となる値
  baseSize: {
    type: Number,
    default: 72,
  },
  // baseSizeの倍数で指定する
  width: {
    type: Number,
    default: 1,
  },
  height: {
    type: Number,
    default: 1,
  },
})

defineEmits(['click']);

const calcWidth = computed(() => {
  return `${props.baseSize * props.width}px`
})

const calcHeight = computed(() => {
  return `${props.baseSize * props.height}px`
})

</script>
