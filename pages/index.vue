<script setup lang="ts">
import LandingSection from '~/components/landing/LandingSection.vue'
import SocialsSection from '~/components/socials/SocialsSection.vue'

defineOgImageScreenshot()
definePageMeta({
  title: 'About',
})
const isYearly = ref(false)
const techs = [
  {
    name: 'i-logos-php',
    title: 'PHP',
    link: 'https://php.com/',
  },
  {
    name: 'i-logos-laravel',
    title: 'Laravel',
    link: 'https://laravel.com/',
  },
  {
    name: 'i-logos-docker-icon',
    title: 'Docker',
    link: 'https://www.docker.com/',
  },
  {
    name: 'i-logos-phpstorm',
    title: 'PhpStorm',
    link: 'https://www.jetbrains.com/phpstorm/',
  },
  {
    name: 'Oauth',
    title: 'OAuth',
    link: 'https://oauth.net/',
  },
  {
    name: 'NovaSvg',
    title: 'Laravel Nova',
    link: 'https://nova.laravel.com/',
  },
  {
    name: 'i-logos-vue',
    title: 'Vue.js',
    link: 'https://vuejs.org/',
  },
  {
    name: 'i-logos-mysql',
    title: 'MySql',
    link: 'https://www.mysql.com/',
  },
  {
    name: 'i-logos-postgresql',
    title: 'PostgreSQL',
    link: 'https://www.postgresql.org/',
  },
  {
    name: 'i-logos-swagger',
    title: 'Swagger',
    link: 'https://swagger.io/',
  },
  {
    name: 'i-logos-redis',
    title: 'Redis',
    link: 'https://redis.io/',
  },
  {
    name: 'i-logos-sentry-icon',
    title: 'Sentry',
    link: 'https://sentry.io/',
  },
]
</script>

<template>
  <UContainer>
    <LandingSection
      icon="i-heroicons-rocket-launch"
      description="CRM для психологов. Удобный и надежный инструмент для управления клиентами и расписанием"
    >
      <template #title>
        <span
          class="text-4xl gap-2 flex flex-col font-bold tracking-tight text-gray-900 dark:text-white sm:text-4xl lg:text-5xl"
        >
          PsychManager
          <span>
            Дневник психолога
          </span>
        </span>
      </template>
    </LandingSection>
    <LandingSection>
      <LandingGrid>
        <LandingCard
          class="col-span-6 row-span-2"
          title="Color Palette"
          description="Choose a primary and a gray color from your Tailwind CSS color palette. Components will be styled accordingly."
          icon="i-heroicons-swatch"
          color="primary"
        />
        <LandingCard
          class="col-span-6 row-span-2"
          title="Color Palette"
          description="Choose a primary and a gray color from your Tailwind CSS color palette. Components will be styled accordingly."
          icon="i-heroicons-swatch"
          color="primary"
        />
        <LandingCard
          class="col-span-6 row-span-2"
          title="Color Palette"
          description="Choose a primary and a gray color from your Tailwind CSS color palette. Components will be styled accordingly."
          icon="i-heroicons-swatch"
          color="primary"
        />
        <LandingCard
          class="col-span-6 row-span-2"
          title="Color Palette"
          description="Choose a primary and a gray color from your Tailwind CSS color palette. Components will be styled accordingly."
          icon="i-heroicons-swatch"
          color="primary"
        />
      </LandingGrid>
    </LandingSection>
    <LandingSection
      title="Developing Accessible Applications with Modern Tech"
      description="CRM для психологов. Удобный и надежный инструмент для управления клиентами и расписанием"
      align="left"
    >
      <div class="grid-cols-3 grid place-items-center gap-y-6">
        <div v-for="(item, index) in techs" :key="index" class="">
          <UTooltip>
            <template #text>
              <span class="flex items-center gap-1">{{ item.title }}
                <UIcon
                  class="text-blue-400"
                  name="i-formkit-linkexternal"
                />
              </span>
            </template>
            <NuxtLink external :to="item.link" target="_blank">
              <Icon :name="item.name" class="text-5xl" />
            </NuxtLink>
          </UTooltip>
        </div>
      </div>
    </LandingSection>
    <UContainer
      class="flex flex-col items-center justify-center gap-10"
    >
      <!--      <PricingGrid> -->
      <PricingToggle
        v-model="isYearly" ggle class="max-w-xs"
      />
      <div>
        <PricingCard
          v-if="!isYearly"
          title="Ежемесячно"
          description="Стоимость месяца подписке при ежемесячной оплате"
          price="1200₽"
          cycle="/мес."
          discount=""
          :badge="{ label: 'Most popular' }"
          :button="{ label: 'Buy now' }"
          orientation="vertical"
          align="bottom"
          :features="['One developer', 'Unlimited projects', 'Unlimited minor & patch updates', 'Lifetime access']"
          scale
          highlight
        />
        <PricingCard
          v-if="isYearly"
          title="Ежегодно"
          description="Стоимость месяца подписке при оплате за год"
          price="1000₽"
          cycle="/мес."
          discount=""
          :badge="{ label: 'Most popular' }"
          :button="{ label: 'Buy now' }"
          orientation="vertical"
          align="bottom"
          :features="['One developer', 'Unlimited projects', 'Unlimited minor & patch updates', 'Lifetime access']"
          scale
          highlight
        />
      </div>
      <!--      </PricingGrid> -->
    </UContainer>

    <LandingSection title="Additional info">
      <template #description>
        <div class="flex flex-col gap-4 items-center">
          <div class="flex items-center">
            <span>
              Currently in Russia, Belgorod
            </span>
            <UIcon class="text-primary" name="i-mdi-location" />
          </div>
          <SocialsSection />
          <div>Hobbies: music 🎸, psychology 🧠, movies 🎬, cats 🐈, coffee ☕ and memes 🗿</div>
        </div>
      </template>
    </LandingSection>
  </UContainer>
</template>
