<script lang="ts" setup>
const props = defineProps<{
  title: string
  content: string
  color: string
  footer: string
}>()

const keys = Object.keys(props.footer) as any[]
</script>

<template>
  <div
    class="flex flex-col rounded-2xl text-white py-5 px-10 gap-2 ali"
    :style="{
      background: props.color,
    }"
  >
    <div class="text-4xl bold">{{ props.title }}</div>
    <div class="text-3xl bold">{{ props.content }}</div>
    <p class="pt-3">
      <span v-for="item in keys" :key="item"
        ><a :href="props.footer[item]" target="_blank">
          > {{ item }} &nbsp;</a
        ></span
      >
    </p>
  </div>
</template>

<style lang="scss" scoped></style>
