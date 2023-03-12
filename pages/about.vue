<script lang="ts" setup>
import { capitalize } from '~/utils/str'

// composable
const { t } = useLang()

// compiler macro
definePageMeta({
  layout: 'page',
})
useHead(() => ({
  title: capitalize(t('pages.about.title')),
  meta: [
    {
      name: 'description',
      content: t('pages.about.description'),
    },
  ],
}))
</script>

<template>
  <PageWrapper>
    <PageHeader>
      <PageTitle
        :text="$t('pages.about.description')"
        :img="'./images/about-banner.png'"
      />
    </PageHeader>
    <PageBody>
      <PageSection>
        <p>水焰团队是一个开源组织，2019 年 8 月创建。</p>
        <p>我们基于开源社区，制作了几个开源项目。</p>
        <p>
          我们将每个项目的制作都投入社区，每个项目都是水焰与社区共创的结果。
        </p>
      </PageSection>
      <PageSection>
        <p>技术因生活而生，技术本就应服务生活。</p>
        <p>用技术便利生活，探索生活命题是我们的最终使命。</p>
        <br />
        <p>开放前行是我们的核心精神。</p>
        <p>以开放的心态不断前行，拥抱社区，不断进步。</p>
        <br />
        <a
          href="https://www.yuque.com/epeiuss/xykong/waterflames-civilization?singleDoc# "
          class="font-bold"
          target="_blank"
        >
          > 阅读文化手册</a
        >
      </PageSection>

      <PageSection class="flex flex-col gap-20">
        <PagePeople
          title="主要成员"
          :content="[
            {
              avatar: './avatars/王淳彧.jpg',
              name: '王淳彧',
              desc: 'WaterFlames 创始人',
              note: {
                BLOG: 'https://www.yuque.com/epeiuss',
                Gitee: 'https://gitee.com/epeiusss',
                GitHub: 'https://github.com/epeiuss',
              },
            },
            {
              avatar: './avatars/折腾调.png',
              name: '折腾调',
              desc: 'WaterFlames 主创人员',
              note: {
                Gitee: 'https://gitee.com/zhetengtiao',
                GitHub: 'https://github.com/zhetengtiao',
              },
            },
          ]"
        ></PagePeople>
        <PagePeople
          title="核心贡献者"
          :content="[
            {
              avatar: './avatars/半糖.webp',
              name: '半糖人类',
              note: {
                GitHub: 'https://github.com/orangelckc',
              },
            },
          ]"
        ></PagePeople>
        <!-- <PagePeople
          title="贡献者"
          :content="[
            {
              name: '绿色耀西',
              note: '> Gitee',
            },
            {
              name: '小鱼yuzifu',
              note: '> Gitee',
            },
            {
              name: 'liulyxandy',
              note: '> Gitee',
            },
            {
              name: 'Zeneks',
              note: '> Gitee',
            },
            {
              name: '更多贡献者',
              note: '点击查看',
            },
          ]"
        ></PagePeople> -->
        <PagePeople
          title="赞助"
          :content="[
            {
              avatar: './avatars/爱发电.png',
              note: {
                爱发电: 'https://afdian.net/a/waterflames',
              },
            },
          ]"
        >
          <div class="text-lg">
            <p>如果你想要支持我们，欢迎给我们赞助。</p>
            <p>每年服务器、域名、cdn等等云资源都会耗费我们很多钱，</p>
            <p>我们迫切需要更多的赞助帮助我们继续支撑团队开销，</p>
            <p>谢谢你。</p>
          </div>
        </PagePeople>
      </PageSection>

      <PageSection>
        <div
          class="rounded-xl flex flex-col w-full p-10 gap-6 md:p-20"
          style="
            background-image: url('./images/about-footer.png');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
          "
        >
          <div
            class="flex flex-col flex-1 text-lg gap-2 ali md:text-4xl md:gap-4 xl:text-6xl"
          >
            <p>关于我们的联系方式？</p>
            <p>这里都可以看到。</p>
          </div>
          <a
            href="https://www.yuque.com/epeiuss/xykong/contact?singleDoc#"
            class="text-sm break-all md:text-base"
            target="_blank"
          >
            https://www.yuque.com/epeiuss/xykong/contact?singleDoc#</a
          >
        </div>
      </PageSection>
    </PageBody>
  </PageWrapper>
</template>
