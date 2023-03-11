<script lang="ts" setup>
import { capitalize } from '~/utils/str'

// composable
const { t } = useLang()

// compiler macro
definePageMeta({
  layout: 'page',
})
useHead(() => ({
  title: capitalize(t('pages.post.title')),
  meta: [
    {
      name: 'description',
      content: t('pages.post.description'),
    },
  ],
}))
</script>

<template>
  <PageWrapper>
    <PageHeader>
      <PageTitle :text="$t('pages.post.title')" class="capitalize" />
    </PageHeader>
    <PageBody>
      <ContentList v-slot="{ list }" path="/post">
        <PageSection v-for="article in list" :key="article._path">
          <div
            class="border rounded flex flex-col border-gray-50/[0.2] py-6 px-4 gap-2 block md:flex-row md:gap-6 hover:no-underline"
          >
            <div
              class="flex flex-row text-gray-500 gap-3 justify-between md:flex-col md:justify-start"
            >
              <div>{{ article.date }}</div>
              <Anchor
                class="flex space-x-1 text-sm items-center justify-start"
                :href="article.link"
              >
                <icon-mdi:github-face class="text-xs" />
                <span>{{ article.author }}</span>
              </Anchor>
            </div>
            <div class="flex flex-col flex-1">
              <div
                class="font-semibold text-xl mb-4 text-slate-800 dark:text-gray-50"
              >
                <Anchor :to="article._path">
                  <span>{{ article.title }}</span>
                </Anchor>
              </div>
              <div class="text-lg mb-1 text-slate-700 dark:text-gray-300">
                {{ article.description }}
              </div>
              <div class="flex">
                <Anchor
                  class="flex space-x-1 text-sm text-primary-500 items-center"
                  :to="article._path"
                >
                  <span>{{ $t('others.learn_more') }}</span>
                  <icon:ic:baseline-arrow-right-alt class="text-sm" />
                </Anchor>
              </div>
            </div>
          </div>
        </PageSection>
      </ContentList>
    </PageBody>
  </PageWrapper>
</template>
