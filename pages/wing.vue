<script lang="ts" setup>
import { capitalize } from '~/utils/str'
import { cdnUrl } from '~/utils/cdn'

// composable
const { t } = useLang()

// compiler macro
definePageMeta({
  layout: 'page',
})
useHead(() => ({
  title: capitalize(t('pages.wing.title')),
  meta: [
    {
      name: 'description',
      content: t('pages.wing.description'),
    },
  ],
}))
const arr = ref([
  {
    title: 'wing-kernel',
    content: 'python生成版',
    content2: '',
  },
  {
    title: 'wing-lite',
    content: 'js生成版',
    content2: '',
  },
])
</script>

<template>
  <PageWrapper>
    <PageHeader>
      <PageTitle
        :text="$t('pages.wing.description') + '[][停止维护]'"
        :img="cdnUrl('wing-banner.png')"
      />
    </PageHeader>
    <PageBody>
      <PageSection>
        <p>Wing 是 WaterFlames 的一个博客制作系统，</p>
        <p>你可以通过简单的配置与 markdown 来构建属于自己的博客。</p>
        <p>现在他们都已不再维护：</p>
      </PageSection>

      <PageSection
        class="flex flex-col flex-wrap gap-10 justify-center items-center lg:flex-row"
      >
        <PageCard
          title="wing-kernel"
          content="python生成版"
          color="linear-gradient(61deg, #6485BF 0%, #9AAAC6 99%)"
          :footer="{
            Gitee: 'https://gitee.com/waterflames-team/wing-kernel',
            Github: 'https://github.com/waterflames-team/wing-kernel',
          }"
        ></PageCard>
        <PageCard
          title="wing-lite"
          content="js生成版"
          color="linear-gradient(61deg, #6485BF 0%, #9AAAC6 99%)"
          :footer="{
            Gitee: 'https://gitee.com/waterflames-team/wing-lite',
            Github: 'https://github.com/waterflames-team/wing-lite',
          }"
        ></PageCard>
      </PageSection>

      <PageSection>
        <div
          class="rounded-xl flex flex-col w-full py-20 px-10 gap-4 justify-center items-center md:flex-row xl:gap-10"
          :style="{
            backgroundImage: `url(${cdnUrl('ringrobotx-footer.png')})`,
            backgroundSize: 'cover',
            backgroundPosition: 'center',
            backgroundRepeat: 'no-repeat',
          }"
        >
          <div
            class="flex flex-col flex-1 text-3xl gap-6 items-center ali lg:text-6xl"
          >
            <p>如果你想的话</p>
            <p>你还可以去看看Wing</p>
          </div>
        </div>
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>
