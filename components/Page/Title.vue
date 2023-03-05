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
  <div class="font-bold leading-normal text-6xl">
    <slot>
      <div
        class="flex flex-col px-20 justify-center"
        :style="{
          backgroundImage: `url(${props.img})`,
          backgroundSize: 'cover',
          backgroundPosition: 'center',
          backgroundRepeat: 'no-repeat',
          height: '800px',
        }"
      >
        <p v-for="item of title" :key="item">{{ item }}</p>
      </div>
    </slot>
  </div>
</template>
