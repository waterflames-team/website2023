<script lang="ts" setup>
import { AppConfigInput } from '@nuxt/schema'

export interface IMenuItem {
  type: 'link' | 'button'
  text: string
  href?: any
  route?: any
}

const { t } = useLang()
const app = useAppConfig() as AppConfigInput
const menus = computed((): IMenuItem[] => [
  {
    type: 'link',
    text: t('pages.ringrobotx.nav'),
    route: { name: 'ringrobotx' },
  },
  {
    type: 'link',
    text: t('pages.wing.nav'),
    route: { name: 'wing' },
  },
  {
    type: 'link',
    text: t('pages.tergamer.nav'),
    route: { name: 'tergamer' },
  },
  { type: 'link', text: t('pages.about.nav'), route: { name: 'about' } },
  { type: 'link', text: t('pages.post.nav'), route: { name: 'post' } },
])
</script>

<template>
  <BuilderNavbar>
    <template #banner>
      <div
        class="bg-[#4f7ce1] text-white text-xs text-center py-1 px-4 capitalize lg:px-8"
      >
        <span class="mr-1">
          {{ $t('banners.welcome') }}
          <Anchor
            class="font-bold ml-10 underline"
            :text="$t('others.learn_more')"
            href="https://afdian.net/item/c851c92ab39011ed998952540025c377"
          />
        </span>
      </div>
    </template>
    <template #menu>
      <div class="ml-auto relative hidden items-center lg:flex">
        <nav
          class="font-semibold text-sm text-gray-600 leading-6 dark:text-gray-300"
          role="navigation"
        >
          <ul class="flex space-x-8 items-center">
            <li v-for="(item, i) in menus" :key="i">
              <Anchor
                v-if="item.type === 'link'"
                :to="item.route ? item.route : undefined"
                :href="item.href ? item.href : undefined"
                class="text-xl capitalize hover:text-slate-900 hover:no-underline hover:dark:text-white"
                >{{ item.text }}</Anchor
              >
              <Button
                v-else-if="item.type === 'button'"
                :text="item.text"
                size="xs"
                class="font-extrabold capitalize"
                :to="item.route ? item.route : undefined"
                :href="item.href ? item.href : undefined"
              />
            </li>
          </ul>
        </nav>
      </div>
    </template>
    <template #options="{ toggleOptions }">
      <ActionSheet @on-close="toggleOptions(false)">
        <ActionSheetBody>
          <nav class="font-semibold text-gray-600 leading-6 dark:text-gray-300">
            <ul class="flex flex-col">
              <li
                v-for="(item, i) in menus"
                :key="i"
                class="flex w-full"
                :class="{
                  'pb-2 mb-2 border-b border-gray-900/10 dark:border-gray-50/[0.2]':
                    item.type === 'link',
                }"
              >
                <Anchor
                  v-if="item.type === 'link'"
                  :to="item.route ? item.route : undefined"
                  :href="item.href ? item.href : undefined"
                  class="flex-1 capitalize hover:no-underline"
                  >{{ item.text }}</Anchor
                >
                <Button
                  v-else-if="item.type === 'button'"
                  :text="item.text"
                  size="xs"
                  class="font-extrabold flex-1 capitalize"
                  :to="item.route ? item.route : undefined"
                  :href="item.href ? item.href : undefined"
                />
              </li>
            </ul>
          </nav>
        </ActionSheetBody>
        <Button
          type="secondary"
          title="Github"
          href="https://github.com/orangelckc/water-flames"
        >
          <IconMdi:github-face />
          <span class="ml-1">Github</span>
        </Button>
        <Button
          text="Close"
          type="secondary"
          @click.prevent="toggleOptions(false)"
        />
      </ActionSheet>
    </template>
  </BuilderNavbar>
</template>
