<script setup lang="ts">
import SocialsSection from '~/components/socials/SocialsSection.vue'
import LandingSection from '~/components/landing/LandingSection.vue'

definePageMeta({
  title: 'Socials',
})
</script>

<template>
  <LandingSection title="Feel free to contact me">
    <template #description>
      <div class="flex flex-col gap-4 items-center">
        <div class="flex items-center">
          <span>
            Currently in Russia, Belgorod
          </span>
          <UIcon class="text-primary" name="i-mdi-location" />
        </div>
        <SocialsSection />
      </div>
    </template>
  </LandingSection>
</template>

<style scoped>

</style>
