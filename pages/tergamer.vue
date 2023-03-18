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
    <!-- <PageHeader class="flex gap-10 items-center">
      <PageTitle
        :text="$t('pages.tergamer.description')"
        img="/images/ringrobotx-banner.png"
      >
        <img src="/images/tergamer-banner.png" class="w-120" />
      </PageTitle>
    </PageHeader> -->
    <PageHeader class="flex gap-10 relative items-center">
      <PageTitle
        :text="$t('pages.tergamer.description')"
        img="/images/ringrobotx-banner.png"
        class="flex-1 w-full top-0 absolute"
      >
        <img :src="cdnUrl('tergamer-banner.png')" class="w-120" />
      </PageTitle>
    </PageHeader>
  </PageWrapper>
</template>
