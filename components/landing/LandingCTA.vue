<script setup lang="ts">
import { twJoin } from 'tailwind-merge'
import type { Button } from '#ui/types'
import type { card as cardConfig } from '#ui/ui.config'

defineOptions({
  inheritAttrs: false,
})

const props = withDefaults(defineProps<{
  title?: string
  description?: string
  card?: boolean
  links?: (Button & { click?: Function })[]
  align?: 'left' | 'center' | 'right'
  ui?: Partial<typeof config.value & typeof cardConfig>
  class?: any
}>(), {
  title: '',
  description: undefined,
  card: true,
  links: () => [],
  align: 'center',
  ui: () => ({}),
  class: undefined,
})

const config = computed(() => {
  const card: Record<string, string> = {}

  if (props.card) {
    card.rounded = 'rounded-xl'
  }
  else {
    card.ring = ''
    card.rounded = ''
    card.background = ''
    card.shadow = ''
    card.divide = ''
  }

  const base = twJoin(
    'flex flex-col',
    props.align !== 'center' && 'lg:grid lg:grid-cols-2 lg:items-center',
    'gap-16 sm:gap-y-24',
  )

  const padding: string = props.card ? 'py-24 sm:py-32 sm:px-16' : 'py-24 sm:py-32 px-6 lg:px-8'

  return {
    ...card,
    wrapper: 'relative',
    body: {
      base,
      padding,
    },
    title: 'text-3xl font-bold tracking-tight text-gray-900 dark:text-white sm:text-4xl',
    description: 'mt-6 text-lg/8 text-gray-600 dark:text-gray-300',
    links: 'mt-10 flex items-center gap-x-6',
  }
})

const { ui, attrs } = useUI('landing.cta', toRef(props, 'ui'), config, toRef(props, 'class'), true)
</script>

<template>
  <UCard :class="ui.wrapper" v-bind="attrs" :ui="ui">
    <div :class="[align === 'center' && 'text-center', align === 'right' && 'lg:order-last']">
      <h2 v-if="title || $slots.title" :class="ui.title">
        <slot name="title">
          {{ title }}
        </slot>
      </h2>

      <p v-if="description || $slots.description" :class="ui.description">
        <slot name="description">
          {{ description }}
        </slot>
      </p>

      <div v-if="links?.length || $slots.links" :class="[ui.links, align === 'center' && 'justify-center']">
        <slot name="links">
          <UButton v-for="(link, index) in links" :key="index" v-bind="link" @click="link.click" />
        </slot>
      </div>
    </div>

    <slot v-if="$slots.default" />
    <div v-else-if="align === 'right'" />
  </UCard>
</template>
