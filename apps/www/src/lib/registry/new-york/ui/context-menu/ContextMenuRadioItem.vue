<script setup lang="ts">
import {
  ContextMenuItemIndicator,
  ContextMenuRadioItem,
  type ContextMenuRadioItemEmits,
  type ContextMenuRadioItemProps,
} from 'radix-vue'
import RadixIconsDotFilled from '~icons/radix-icons/dot-filled'
import { cn, useEmitAsProps } from '@/lib/utils'

const props = defineProps<ContextMenuRadioItemProps & { class?: string }>()
const emits = defineEmits<ContextMenuRadioItemEmits>()
</script>

<template>
  <ContextMenuRadioItem
    v-bind="{ ...props, ...useEmitAsProps(emits) }"
    :class="[
      cn(
        'relative flex cursor-default select-none items-center rounded-sm py-1.5 pl-8 pr-2 text-sm outline-none focus:bg-accent focus:text-accent-foreground data-[disabled]:pointer-events-none data-[disabled]:opacity-50',
        props.class,
      ),
    ]"
  >
    <span class="absolute left-2 flex h-3.5 w-3.5 items-center justify-center">
      <ContextMenuItemIndicator>
        <RadixIconsDotFilled class="h-4 w-4 fill-current" />
      </ContextMenuItemIndicator>
    </span>
    <slot />
  </ContextMenuRadioItem>
</template>
