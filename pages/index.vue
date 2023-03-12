<script lang="ts" setup>
// composable
const { t } = useLang()

// meta
definePageMeta({
  layout: 'page',
})

// vars
const titlesText = (str: string) => {
  return t(str).split('[]')
}
</script>

<template>
  <PageWrapper class="flex flex-col flex-1 px-5 gap-5 justify-center lg:px-35">
    <PageSection
      class="flex rounded-2xl flex-1 py-40 items-center"
      :style="{
        backgroundImage: `url('/images/index-banner.png')`,
        backgroundSize: 'cover',
        backgroundPosition: 'center',
        backgroundRepeat: 'no-repeat',
      }"
    >
      <div class="flex flex-col flex-1 z-10 md:pl-20 md:w-5/8">
        <h1
          class="flex flex-col mt-4 text-white text-center gap-6 md:text-left"
        >
          <span
            v-for="(item, i) in titlesText('pages.index.title')"
            :key="i"
            class="font-black text-3xl ali drop-shadow-xl block md:text-4xl xl:text-5xl 2xl:text-7xl"
            :class="{
              'text-5xl md:text-6xl xl:text-7xl 2xl:text-8xl': i === 0,
            }"
          >
            <span>{{ item }}</span>
          </span>
        </h1>
        <div class="flex space-x-4 mt-20 justify-center md:justify-start">
          <Button
            size="lg"
            text="Gitee"
            type="opposite"
            class="font-extrabold"
            href="https://gitee.com/waterflames-team/"
          />
          <Button
            size="lg"
            text="Github"
            type="opposite"
            class="font-extrabold"
            href="https://github.com/waterflames-team/"
          />
        </div>
      </div>
    </PageSection>
    <PageSection
      class="flex rounded-2xl flex-1 py-20 items-center"
      :style="{
        backgroundImage: `url('/images/ringrobotx-banner.png')`,
        backgroundSize: 'cover',
        backgroundPosition: 'center',
        backgroundRepeat: 'no-repeat',
      }"
    >
      <div class="flex flex-col flex-1 z-10 md:pl-20 md:w-5/8">
        <h1
          class="flex flex-col mt-4 text-white text-center gap-6 md:text-left"
        >
          <span
            v-for="(item, i) in titlesText('pages.ringrobotx.description')"
            :key="i"
            class="font-black text-3xl ali drop-shadow-xl block md:text-4xl xl:text-5xl 2xl:text-7xl"
            :class="{
              'text-5xl md:text-6xl xl:text-7xl 2xl:text-8xl': i === 0,
            }"
          >
            <span>{{ item }}</span>
          </span>
        </h1>
        <div class="flex mt-20 justify-center md:justify-start">
          <Button
            size="lg"
            text="项目介绍"
            type="opposite"
            class="font-extrabold"
            to="/ringrobotx"
          />
        </div>
      </div>
    </PageSection>
    <PageSection
      class="flex flex-col rounded-2xl flex-1 py-20 gap-10 items-center justify-center md:flex-row md:flex-1"
      :style="{
        backgroundImage: `url('/images/ringrobotx-banner.png')`,
        backgroundSize: 'cover',
        backgroundPosition: 'center',
        backgroundRepeat: 'no-repeat',
      }"
    >
      <div class="flex flex-col flex-1 z-10 md:pl-20 md:w-5/8">
        <h1
          class="flex flex-col mt-4 text-white text-center gap-6 md:text-left"
        >
          <span
            v-for="(item, i) in titlesText('TerGamer[]与我们一同开发')"
            :key="i"
            class="font-black text-3xl ali drop-shadow-xl block md:text-4xl xl:text-5xl 2xl:text-7xl"
            :class="{
              'text-5xl md:text-6xl xl:text-7xl 2xl:text-8xl': i === 0,
            }"
          >
            <span>{{ item }}</span>
          </span>
        </h1>
        <div class="flex mt-20 justify-center md:justify-start">
          <Button
            size="lg"
            text="Gitee"
            type="opposite"
            class="font-extrabold"
            href="https://gitee.com/waterflames-team/ter-gamer"
          />
        </div>
      </div>
      <img src="/images/tergamer-banner.png" class="w-120" />
    </PageSection>
    <PageSection
      class="flex rounded-2xl flex-1 py-20 items-center"
      :style="{
        backgroundImage: `url('/images/wing-banner.png')`,
        backgroundSize: 'cover',
        backgroundPosition: 'center',
        backgroundRepeat: 'no-repeat',
      }"
    >
      <div class="flex flex-col flex-1 z-10 md:pl-20 md:w-5/8">
        <h1
          class="flex flex-col mt-4 text-white text-center gap-6 md:text-left"
        >
          <span
            v-for="(item, i) in titlesText('pages.wing.description')"
            :key="i"
            class="font-black text-3xl ali drop-shadow-xl block md:text-4xl xl:text-5xl 2xl:text-7xl"
            :class="{
              'text-5xl md:text-6xl xl:text-7xl 2xl:text-8xl': i === 0,
            }"
          >
            <span>{{ item }}</span>
          </span>
        </h1>
        <div class="flex mt-20 justify-center md:justify-start">
          <Button
            size="lg"
            text="项目介绍"
            type="opposite"
            class="font-extrabold"
            to="/wing"
          />
        </div>
      </div>
    </PageSection>
    <PageSection
      class="flex rounded-2xl flex-1 py-20 items-center"
      :style="{
        backgroundImage: `url('/images/about-banner.png')`,
        backgroundSize: 'cover',
        backgroundPosition: 'center',
        backgroundRepeat: 'no-repeat',
      }"
    >
      <div class="flex flex-col flex-1 z-10 md:pl-20 md:w-5/8">
        <h1
          class="flex flex-col mt-4 text-white text-center gap-6 md:text-left"
        >
          <span
            v-for="(item, i) in titlesText('pages.about.description')"
            :key="i"
            class="font-black text-3xl ali drop-shadow-xl block md:text-4xl xl:text-5xl 2xl:text-7xl"
            :class="{
              'text-5xl md:text-6xl xl:text-7xl 2xl:text-8xl': i === 0,
            }"
          >
            <span>{{ item }}</span>
          </span>
        </h1>
        <div class="flex mt-20 justify-center md:justify-start">
          <Button
            size="lg"
            text="项目介绍"
            type="opposite"
            class="font-extrabold"
            to="/about"
          />
        </div>
      </div>
    </PageSection>
  </PageWrapper>
</template>

<style lang="scss">
@import '../assets/sass/variables';

@keyframes anim-fg-1 {
  0%,
  16.667%,
  100% {
    opacity: 1;
  }

  33.333%,
  83.333% {
    opacity: 0;
  }
}

@keyframes anim-fg-2 {
  0%,
  16.667%,
  66.667%,
  100% {
    opacity: 0;
  }

  33.333%,
  50% {
    opacity: 1;
  }
}

@keyframes anim-fg-3 {
  0%,
  50%,
  100% {
    opacity: 0;
  }

  66.667%,
  83.333% {
    opacity: 1;
  }
}

.animated-text-bg {
  position: relative;
  display: block;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  content: var(--content);
  display: block;
  width: 100%;
  color: theme('colors.slate.800');
  top: 0;
  bottom: 0;
  left: 0;
  z-index: 0;
  padding-left: $padding;
  padding-right: $padding;
  &:before {
    content: var(--content);
    position: absolute;
    display: block;
    width: 100%;
    color: theme('colors.slate.800');
    top: 0;
    bottom: 0;
    left: 0;
    z-index: 0;
    padding-left: $padding;
    padding-right: $padding;
  }
}
.animated-text-fg {
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  padding-left: $padding;
  padding-right: $padding;
  background-image: linear-gradient(
    90deg,
    var(--start-color),
    var(--end-color)
  );
  position: relative;
  opacity: 0;
  z-index: 1;
  animation: var(--animation-name) 8s infinite;
}

html.dark {
  .animated-text-bg {
    color: theme('colors.gray.100');
    &:before {
      color: theme('colors.gray.100');
    }
  }
}

.triangle-shape {
  width: 0;
  height: 0;
  border-left: 25px solid transparent;
  border-right: 25px solid transparent;
  border-bottom: 40px solid theme('colors.green.600');
  transform: translate(-15rem, -6rem) rotate(45deg);
}

.tooltip {
  position: relative;
  display: inline-block;
}

.tooltip .tooltiptext {
  visibility: hidden;
  width: 140px;
  background-color: #555;
  color: #fff;
  text-align: center;
  border-radius: 6px;
  padding: 5px;
  position: absolute;
  z-index: 1;
  bottom: 150%;
  left: 50%;
  margin-left: -75px;
  opacity: 0;
  transition: opacity 0.3s;
}

.tooltip .tooltiptext::after {
  content: '';
  position: absolute;
  top: 100%;
  left: 50%;
  margin-left: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: #555 transparent transparent transparent;
}

.tooltip:hover .tooltiptext {
  visibility: visible;
  opacity: 1;
}
</style>
