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
      name: 'keywords',
      content:
        '开源, WaterFlames, RingRobotX, Wing, TerGamer, 探索生活命题, waterflames, ringrobotx, wing, tergamer',
    },
    {
      name: 'description',
      content:
        'WaterFlames, 一个开放开源的团队, 致力于探索生活命题|RingRobotX, 一个采用单轮对话设计的, 中文模块化语音机器人框架|Wing, 让你用简单的配置, 制作属于自己的博客|TerGamer, 一个命令行游戏框架[]它还在开发, 如果你想的话可以和我们一起|关于我们, 共同探索生活命题',
    },
  ],
  link: [{ rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' }],
  script: [
    // Google Analytics Code
    {
      src: 'https://www.googletagmanager.com/gtag/js?id=G-5DPSXPCFB3',
      async: true,
    },
    // Import analitics.js file
    { src: '/static/js/analytics.js' },
  ],
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
