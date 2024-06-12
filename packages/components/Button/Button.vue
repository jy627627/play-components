<script setup lang="ts">
// Button.vue, Button.test.tsx(测试用例), type.ts, style.css, constants.ts(常量)
import type { ButtonProps } from "./type.ts";
import { ref } from "vue";

defineOptions({
  name: 'ErButton',
})

const props = withDefaults(defineProps<ButtonProps>(), {
  tag: 'button',
  nativeType: 'button',
})

const slots = defineSlots()

const _ref = ref<HTMLButtonElement>()

</script>

<template>
  <component
      :is="props.tag"
      ref="_ref"
      class="er-button"
      :type="tag === 'button' ? nativeType : void 0"
      :disabled="disabled || loading ? true : void 0"
      :class="{
      [`er-button--${type}`]: type,
      [`er-button--${size}`]: size,
      'is-plain':plain,
      'is-round':round,
      'is-circle':circle,
      'is-disabled':disabled,
      'is-loading':loading,
    }"
  >
    <slot></slot>
  </component>
</template>

<style scoped>
@import "style.css";
</style>
