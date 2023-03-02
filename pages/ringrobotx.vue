<script lang="ts" setup>
import { capitalize } from '~/utils/str'

// composable
const { t } = useLang()

// compiler macro
definePageMeta({
  layout: 'page',
})
useHead(() => ({
  title: capitalize(t('pages.ringrobotx.title')),
  meta: [
    {
      name: 'description',
      content: t('pages.ringrobotx.description'),
    },
  ],
}))
</script>

<template>
  <PageWrapper>
    <PageHeader>
      <PageTitle :text="$t('pages.ringrobotx.title')" class="capitalize" />
    </PageHeader>
    <PageBody>
      <PageSection>
        <div v-for="i in 3" :key="i" class="text-6xl uppercase">
          {{ $t('pages.ringrobotx.description') }}
          今天是星期{{ i }}
        </div>
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>
