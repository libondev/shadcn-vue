<script setup lang="ts">
import type { SliderRootEmits, SliderRootProps } from 'radix-vue'
import { SliderRange, SliderRoot, SliderThumb, SliderTrack } from 'radix-vue'
import { cn, useEmitAsProps } from '@/lib/utils'

const props = defineProps<SliderRootProps>()
const emits = defineEmits<SliderRootEmits>()
</script>

<template>
  <SliderRoot
    :class="cn(
      'relative flex w-full touch-none select-none items-center',
      $attrs.class ?? '',
    )"
    v-bind="{ ...props, ...useEmitAsProps(emits) }"
  >
    <SliderTrack class="relative h-2 w-full grow overflow-hidden rounded-full bg-secondary">
      <SliderRange class="absolute h-full bg-primary" />
    </SliderTrack>
    <SliderThumb class="block h-5 w-5 rounded-full border-2 border-primary bg-background ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50" />
  </SliderRoot>
</template>
