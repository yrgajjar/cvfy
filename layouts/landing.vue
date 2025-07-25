<script lang="ts" setup>
const CVFY_IMAGE = 'https://www.yags.in/web/image/3393-ff486a32/YagsCV.png?height=256'

const { locale, t } = useI18n()
const route = useRoute()
const localePath = useLocalePath()
const HREF = `https://cv.yags.in${route.path}`
const GITHUB = 'https://github.com/yrgajjar/cvfy'

useHead({
  htmlAttrs: {
    lang: locale,
  },
  title: t(String(route.meta.titleI18n)),
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
      content: 'Yags',
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
      content: 'Yags',
    },
    {
      name: 'twitter:url',
      content: HREF,
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
  <div class="font-landing max-w-screen-xl mx-auto text-fl-xs text-slate-800">
    <header class="p-fl-sm mb-fl-md">
      <nav
        class="font-light flex justify-between items-center"
      >
        <LandingLogo />
        <!-- Disable until more pages available -->
         <section
          class="[grid-area:links] justify-self-center flex gap-fl-lg underline sm:decoration-transparent"
        >
          <LandingLink
            v-for="link in navLinks"
            :key="link.name"
            :to="link.to"
          >
            {{ link.name }}
          </LandingLink>
        </section>
        <section class="flex gap-fl-xs">
     
       
          <LandingLangSwitch />
          <LandingLink
            :to="localePath('create')"
            cta
          >
            {{ $t('create-cv') }}
          </LandingLink>
        </section>
      </nav>
    </header>
    <main class="flex">
      <slot />
    </main>
  </div>
</template>
