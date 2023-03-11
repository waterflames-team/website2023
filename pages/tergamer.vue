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
    <PageHeader class="flex gap-10 items-center">
      <PageTitle
        :text="$t('pages.tergamer.description')"
        img="/images/ringrobotx-banner.png"
      >
        <img src="/images/tergamer-banner.png" class="w-140" />
      </PageTitle>
    </PageHeader>
  </PageWrapper>
</template>

<style lang="scss" scoped>
//TODO 磨砂效果
</style>
