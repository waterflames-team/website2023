<script lang="ts" setup>
import { capitalize } from '~/utils/str'
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
const tooltip = ref(false)

// const
const cancelTooltip = () => {
  tooltip.value = false
  const tt = document.querySelector('.tooltiptext')
  if (tt) tt.innerHTML = `一键复制`
}
const copyBash = () => {
  const bash =
    'wget -O install.sh https://gitee.com/waterflames-team/ring-robot-x/raw/master/install.sh && sudo bash install.sh'
  navigator.clipboard.writeText(bash)
  tooltip.value = true
  const tt = document.querySelector('.tooltiptext')
  if (tt) tt.innerHTML = `已复制`
}

const arr = [
  {
    title: '技能高灵活度',
    content1: '通过技能包管理器',
    content2: '你可以自由安装任何技能',
  },
  {
    title: '简单易配置',
    content1: '配置文件提前抽离',
    content2: '修改用户信息无需打开源代码',
  },
  {
    title: '支持连续对话',
    content1: '我们实现了连续对话',
    content2: '你可以快乐地玩成语接龙了',
  },
  {
    title: '接入简单',
    content1: '我们提供了开放接口',
    content2: '想自己做技能？没问题！',
  },
]
</script>

<template>
  <PageWrapper class="bg-white">
    <PageHeader>
      <PageTitle
        :text="$t('pages.ringrobotx.description')"
        :img="'./images/ringrobotx-banner.png'"
      />
    </PageHeader>
    <PageBody class="flex flex-col p-20 gap-10">
      <PageSection class="text-black text-xl">
        <p>RingRobotX 是 WaterFlames 的一大重点项目群，</p>
        <p>
          我们希望通过这个项目群实现语音对话机器人服务人的场景。 目前 RingRobotX
        </p>
        <p>项目群下已公开以下项目：</p>
      </PageSection>

      <PageSection class="flex justify-between">
        <PageCard
          title="RingRobotX"
          content="项目主仓库"
          color="linear-gradient(61deg, #F17146 0%, #FCE3DA 99%)"
          footer=">文档 > Gitee > Github"
        ></PageCard>
        <PageCard
          title="Mariner"
          content="技能包管理器"
          color="linear-gradient(61deg, #F17146 0%, #FCE3DA 99%)"
          footer=">文档 > Gitee > Github"
        ></PageCard>
      </PageSection>

      <PageSection class="text-black text-xl">
        <p>同时，</p>
        <p>我们在对本项目群展开探索之前也进行了一些实验，</p>
        <p>现在他们都已不再维护：</p>
      </PageSection>

      <PageSection class="flex justify-between">
        <PageCard
          title="lk-robot"
          content="主项目前身"
          color="linear-gradient(0deg, rgba(0, 0, 0, 0.2), rgba(0, 0, 0, 0.2)), linear-gradient(61deg, #5F92EC 0%, #DFE9FB 99%)"
          footer=" > Gitee > Github"
        ></PageCard>
        <PageCard
          title="robot-server"
          content="无语言版本"
          color="linear-gradient(0deg, rgba(0, 0, 0, 0.2), rgba(0, 0, 0, 0.2)), linear-gradient(61deg, #5F92EC 0%, #DFE9FB 99%)"
          footer=" > Gitee > Github"
        ></PageCard>
      </PageSection>

      <PageSection>
        <div
          class="rounded-xl text-white w-full p-10"
          style="
            background-image: url('./images/ringrobotx-feature.png');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
          "
        >
          <div class="flex flex-col gap-1 items-center">
            <p class="text-4xl">特色功能</p>
            <p class="text-lg">至目前开发的版本，我们已有以下特色功能</p>
          </div>
          <div class="flex flex-wrap mt-6 gap-8 justify-around">
            <div
              v-for="item in arr"
              :key="item.title"
              class="bg-black rounded-xl flex flex-col bg-opacity-60 flex-1/2 p-8 w-90 items-center justify-center"
            >
              <p class="text-3xl">{{ item.title }}</p>
              <p class="text-lg">{{ item.content1 }}</p>
              <p class="text-lg">{{ item.content2 }}</p>
            </div>
          </div>
        </div>
      </PageSection>
      <PageSection>
        <div
          class="rounded-xl flex w-full py-20 justify-around"
          style="
            background-image: url('./images/ringrobotx-footer.png');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
          "
        >
          <div class="flex flex-col text-white text-6xl gap-6">
            <p>RingRobotX，</p>
            <p>马上开耍。</p>
          </div>
          <div
            class="hidden justify-center items-end relative md:flex md:w-3/8"
          >
            <div
              class="h-auto border-white-300 border-2 rounded-5px shadow ml-4 w-100 z-10"
            >
              <div
                class="rounded-t-lg flex space-x-4 bg-gray-200 border-b-2 border-gray-300/75 py-2 px-3 win-header relative dark:bg-slate-800 dark:border-slate-700/75"
              >
                <div class="flex space-x-1 win-controls items-center">
                  <div class="rounded-full bg-red-500 h-3 w-3" />
                  <div class="rounded-full bg-green-500 h-3 w-3" />
                  <div class="rounded-full bg-yellow-500 h-3 w-3" />
                </div>
                <div class="font-bold flex-1 text-center text-sm pr-12">
                  BASH
                </div>
                <div class="flex text-sm justify-center items-center">
                  <div class="tooltip">
                    <button
                      class="flex text-gray-100 justify-center items-center"
                      @click="copyBash"
                      @mouseout="cancelTooltip"
                    >
                      <span class="tooltiptext">一键复制</span>
                      <icon-material-symbols:content-copy-outline />
                    </button>
                  </div>
                </div>
              </div>
              <div
                class="rounded-b-lg font-mono bg-gray-200/90 text-sm py-2 px-3 win-body backdrop-filter backdrop-blur-lg dark:bg-slate-800/90"
              >
                <div>
                  $ wget -O install.sh
                  https://gitee.com/waterflames-team/ring-robot-x/raw/master/install.sh
                  && sudo bash install.sh
                </div>
              </div>
            </div>
          </div>
        </div>
      </PageSection>
    </PageBody>
    <PageHeader> </PageHeader>
  </PageWrapper>
</template>
