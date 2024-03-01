<script setup>
import ColorModeButton from '~/components/colorMode/ColorModeButton.vue'

const links = [
  {
    label: 'Попробовать бесплатно',
    icon: 'i-heroicons-book-open',
    to: 'https://panel.psych-manager.ru',

  },
  {
    label: 'Узнать подробности',
    icon: 'i-simple-icons-telegram',
    to: 'https://t.me/psych_manager',
  },
]
</script>

<template>
  <header class="bg-background/75 backdrop-blur  -mb-px sticky top-0 z-50">
    <UContainer class="flex items-center justify-between gap-3 h-[60px]">
      <div class="lg:flex-1 flex items-center gap-1.5">
        <NuxtLink
          aria-label="logo" to="/"
          class="flex-shrink-0 font-bold text-xl text-gray-900 dark:text-white flex items-center gap-1.5"
        >
          <UAvatar
            src="https://avatars.githubusercontent.com/u/36007880?v=4"
            alt="Dmitry Gaponenko"
          />
          <span class="hidden lg:flex">
            Dmitry Gaponenko
          </span>
        </NuxtLink>
      </div>
      <div>
        <ul class="flex items-center gap-x-8">
          <li v-for="(link, index) in links" :key="index" :class="link.disabled ? 'cursor-not-allowed' : ''">
            <NuxtLink
              rel="''"
              active-class="text-primary"
              inactive-class="hover:text-primary "
              class="text-sm/6 font-semibold flex items-center gap-1 text-gray-500"
              :class="link.disabled ? 'pointer-events-none text-gray-400' : ''"
              :disabled="link.disabled"
              :to="{
                path: link.to,
              }"
            >
              <UIcon :name="link.icon" />
              {{ link.label }}
            </NuxtLink>
          </li>
        </ul>
      </div>
      <div class="flex items-center justify-end lg:flex-1 gap-1.5">
        <ColorModeButton />
      </div>
    </UContainer>
  </header>
</template>
