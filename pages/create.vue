<script setup lang="ts">
import { useCvState } from '~/data/useCvState'

const CVFY_IMAGE = 'https://www.yags.in/web/image/3393-ff486a32/YagsCV.png'

const { setUpCvSettings } = useCvState()
const route = useRoute()
const { t, locale } = useI18n()

const href = `https://me.yags.in${route.path}`

onMounted(() => {
  setUpCvSettings()
})

useHead({
  htmlAttrs: {
    lang: locale,
  },
  title: t('title-tag'),
  link: [
   
    {
      rel: 'canonical',
      href,
    },
  ],
  meta: [
    {
      name: 'description',
      content: t('description'),
    },
    {
      name: 'author',
      content: 'yrgajjar',
    },
    {
      property: 'og:image',
      content: CVFY_IMAGE,
    },
    {
      property: 'og:author',
      content: 'Yags',
    },
    {
      property: 'og:title',
      content: t('title-tag'),
    },
    {
      property: 'og:description',
      content: t('description'),
    },
    {
      name: 'twitter:creator',
      content: '@yrgajjar',
    },
    {
      name: 'twitter:title',
      content: t('title-tag'),
    },
    {
      name: 'twitter:url',
      content: href,
    },
    {
      name: 'twitter:description',
      content: t('description'),
    },
    {
      name: 'twitter:card',
      content: 'summary_large_image',
    },
    {
      name: 'twitter:image',
      content: CVFY_IMAGE,
    },
    {
      name: 'twitter:image:alt',
      content: t('description'),
    },
  ],
})
</script>

<template>
  <main class="font-app main">
    <CvSettings class="basis-1/4 min-w-80" />
    <CvPreview class="basis-3/4" />
  </main>
</template>

<style lang="postcss">
@import '@/assets/styles/form.postcss';
@media screen and (min-width: 1024px) {
  .main {
    @apply flex h-screen overflow-hidden;
  }
}
</style>
