<script lang="ts" setup>
import { AppConfigInput } from '@nuxt/schema'
import p from './../../package.json'
const app = useAppConfig() as AppConfigInput
</script>

<template>
  <footer class="border-t lg:border-gray-900/10 dark:border-gray-50/[0.2]">
    <section
      class="flex mx-auto space-x-20 flex-1 w-full max-w-8xl px-4 justify-center lg:px-8"
    >
      <div class="text-center py-4">
        <div class="text-xs text-gray-600 dark:text-gray-400">
          {{ app.name }} ©2019-2023. All rights reserved. <br />Made by
          <a href="" target="_blank">waterflames/webside</a> with
          <span class="text-red-500">❤</span>
        </div>
      </div>
    </section>
  </footer>
</template>
