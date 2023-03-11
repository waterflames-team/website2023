<script lang="ts" setup>
import { text } from 'stream/consumers'

const props = defineProps({
  text: {
    type: String,
    default: '',
  },
  img: {
    type: String,
    default: '',
  },
})

const title = computed(() => {
  return props.text.split('[]')
})
</script>

<template>
  <div
    class="font-bold flex-1 leading-relaxed text-3xl lg:leading-relaxed lg:text-6xl xl:leading-loose"
  >
    <div
      class="flex flex-col h-200 px-10 gap-10 justify-center items-center md:flex-row md:flex-1"
      :style="{
        backgroundImage: `url(${props.img})`,
        backgroundSize: 'cover',
        backgroundPosition: 'center',
        backgroundRepeat: 'no-repeat',
      }"
    >
      <div class="ali">
        <p v-for="item of title" :key="item">{{ item }}</p>
      </div>
      <slot class="bg-red" />
    </div>
  </div>
</template>
