<template>
  <BuilderNavbar>
    <template #menu>
      <div class="ml-auto relative hidden items-center lg:flex">
        <div class="flex items-center justify-center">
          <img
            class="rounded-full h-6 w-6"
            src="https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=634&q=80"
            alt="Avatar of Jonathan Reinink"
          />
          <span class="font-semibold text-sm ml-2">Alfian</span>
          <IconUil:angle-down />
        </div>
        <div
          class="border-l flex space-x-4 border-gray-900/10 ml-6 pl-6 dark:border-gray-50/[0.2]"
        >
          <LanguageSwitcher />
          <ThemeSwitcher />
          <Anchor
            class="flex text-lg self-center items-center hover:text-slate-900 hover:no-underline hover:dark:text-white"
            href="https://github.com/orangelckc/water-flames"
            title="Github"
          >
            <IconMdi:github-face />
          </Anchor>
        </div>
      </div>
    </template>
    <template #options="{ toggleOptions }">
      <ActionSheet @on-close="toggleOptions(false)">
        <ActionSheetBody>
          <ActionSheetHeader text="Menu" />
          <div class="font-bold mt-6 text-sm capitalize">
            {{ $t('components.theme_switcher.change_theme') }}
          </div>
          <div class="mt-2">
            <ThemeSwitcher type="select-box" />
          </div>
          <div class="font-bold mt-6 text-sm capitalize">
            {{ $t('components.language_switcher.change_language') }}
          </div>
          <div class="mt-2">
            <LanguageSwitcher type="select-box" />
          </div>
        </ActionSheetBody>
        <Button
          type="secondary"
          title="Github"
          href="https://github.com/orangelckc/water-flames"
        >
          <IconMdi:github-face />
          <span class="ml-1">Github</span>
        </Button>
        <Button
          text="Close"
          type="secondary"
          @click.prevent="toggleOptions(false)"
        />
      </ActionSheet>
    </template>
    <template #drawer>
      <slot name="drawer" />
    </template>
  </BuilderNavbar>
</template>
