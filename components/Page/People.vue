<script lang="ts" setup>
const props = defineProps<{
  title: string
  content: [
    {
      avatar?: string
      name: string
      desc?: string
      note: string
    }
  ]
}>()
</script>

<template>
  <div class="text-black w-full pr-60">
    <p class="font-bold mb-5 text-5xl">{{ props.title }}</p>
    <slot />
    <div class="flex mt-5 justify-between">
      <div
        v-for="item in content"
        :key="item.name"
        class="flex gap-4 items-center"
      >
        <img
          v-if="item.avatar"
          :src="item.avatar"
          alt=""
          class="rounded-full h-20 w-20"
        />
        <div class="flex flex-col text-2xl">
          <p class="font-bold">{{ item.name }}</p>
          <p>{{ item?.desc }}</p>
          <p>{{ item?.note }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
