<script lang="ts" setup>
import { AppConfigInput } from '@nuxt/schema'
import { AppSetup } from './utils/app'
import { ITheme } from './utils/theme'
AppSetup()
const theme = useState<ITheme>('theme.current')
const locale = useState<string>('locale.setting')
const app = useAppConfig() as AppConfigInput

useHead({
  title: app.name,
  titleTemplate: '%s',
  meta: [
    { name: 'viewport', content: 'width=device-width, initial-scale=1' },
    {
      hid: 'description',
      name: 'description',
      content: 'WaterFlames, 一个开放开源的团队, 致力于探索生活命题',
    },
    {
      name: 'keywords',
      content: 'WaterFlames, RingRobotX, Wing, TerGamer, 探索生活命题',
    },
  ],
  link: [{ rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' }],
})
</script>

<template>
  <Html :class="`${theme === 'dark' ? 'dark' : ''}`" :lang="locale">
    <Body
      class="bg-white transition-colors text-gray-800 overflow-y-scroll antialiased dark:bg-gray-900 dark:text-gray-200"
    >
      <NuxtLayout class="relative" style="background: #151b43">
        <NuxtLoadingIndicator :height="5" :duration="30000" :throttle="400" />
        <NuxtPage />
      </NuxtLayout>
    </Body>
  </Html>
</template>

<!-- <style>
* {
  font-family: 'alimama';
}
</style> -->
