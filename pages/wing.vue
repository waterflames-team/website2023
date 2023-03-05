<script lang="ts" setup>
import { capitalize } from '~/utils/str'

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
  <PageWrapper class="bg-white">
    <PageHeader>
      <PageTitle
        :text="$t('pages.wing.description')"
        :img="'./images/wing-banner.png'"
      />
    </PageHeader>
    <PageBody class="flex flex-col p-20 gap-10">
      <PageSection class="text-black text-xl">
        <p>Wing 是 WaterFlames 的一个博客制作系统，</p>
        <p>你可以通过简单的配置与 markdown 来构建属于自己的博客。</p>
        <p>现在他们都已不再维护：</p>
      </PageSection>

      <PageSection class="flex justify-between">
        <PageCard
          title="wing-kernel"
          content="python生成版"
          color="linear-gradient(61deg, #6485BF 0%, #9AAAC6 99%)"
          footer="> Gitee > Github"
        ></PageCard>
        <PageCard
          title="wing-lite"
          content="js生成版"
          color="linear-gradient(61deg, #6485BF 0%, #9AAAC6 99%);"
          footer="> Gitee > Github"
        ></PageCard>
      </PageSection>

      <PageSection>
        <div
          class="rounded-xl flex flex-col text-white w-full p-20 text-6xl gap-6"
          style="
            background-image: url('./images/ringrobotx-footer.png');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
          "
        >
          <p>如果你想的话，</p>
          <p>你还可以去看看Wing。</p>
        </div>
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>
