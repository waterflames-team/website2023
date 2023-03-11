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
  <div class="font-bold leading-normal text-3xl lg:leading-relaxed lg:text-6xl">
    <slot>
      <div
        class="flex flex-col h-200 pl-5 justify-center items-center lg:pl-100 lg:items-start"
        :style="{
          backgroundImage: `url(${props.img})`,
          backgroundSize: 'cover',
          backgroundPosition: 'center',
          backgroundRepeat: 'no-repeat',
        }"
      >
        <p v-for="item of title" :key="item">{{ item }}</p>
      </div>
    </slot>
  </div>
</template>
