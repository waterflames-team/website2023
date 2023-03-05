<script lang="ts" setup>
import { capitalize } from '~/utils/str'

// composable
const { t } = useLang()

// compiler macro
definePageMeta({
  layout: 'page',
})
useHead(() => ({
  title: capitalize(t('pages.tergamer.title')),
  meta: [
    {
      name: 'description',
      content: t('pages.tergamer.description'),
    },
  ],
}))

const text = computed(() => {
  return t('pages.tergamer.description').split('[]')
})
</script>

<template>
  <PageWrapper>
    <PageBody
      class="flex px-20 items-center"
      :style="{
        backgroundImage: `url('/images/ringrobotx-banner.png')`,
        backgroundSize: 'cover',
        backgroundPosition: 'center',
        backgroundRepeat: 'no-repeat',
        height: '900px',
        marginTop: '-100px',
      }"
    >
      <PageSection>
        <div
          class="flex flex-col font-bold leading-normal text-6xl justify-center"
        >
          <p v-for="item of text" :key="item">{{ item }}</p>
        </div>
      </PageSection>

      <PageSection>
        <div
          class="bg-blue flex flex-col font-bold text-white leading-normal text-4xl"
        >
          <p>制作更简洁</p>
          <p>的游戏产物</p>
          <p>TerGamer</p>
          <p>By WaterF</p>
          <p>terFlames</p>
        </div>
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>

<style lang="scss" scoped>
//TODO 磨砂效果
</style>
