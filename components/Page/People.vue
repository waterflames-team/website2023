<script lang="ts" setup>
const props = defineProps<{
  title: string
  content: [
    {
      avatar?: string
      name: string
      desc?: string
      note: Record<string, any>
    }
  ]
}>()

const getKeys = (note: Record<string, any>) => {
  const keys = Object.keys(note) as any[]
  return keys
}
</script>

<template>
  <div class="w-full">
    <p class="font-bold mb-5 text-3xl ali md:text-5xl">{{ props.title }}</p>
    <slot />
    <div class="flex flex-wrap mt-6 gap-8 md:flex-row">
      <div
        v-for="item in content"
        :key="item.name"
        class="flex gap-4 items-center"
      >
        <img
          v-if="item.avatar"
          :src="item.avatar"
          alt="LOGO"
          class="rounded-full h-15 w-15 md:h-20 md:w-20"
        />
        <div class="flex flex-col text-xl">
          <p class="font-bold">{{ item.name }}</p>
          <p>{{ item?.desc }}</p>
          <p>
            <span v-for="otem in getKeys(item?.note)" :key="otem" class="ali"
              ><a :href="item?.note[otem]" target="_blank">
                > {{ otem }} &nbsp;</a
              ></span
            >
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
