<script lang="ts" setup>
import { AppConfigInput } from '@nuxt/schema'

// state
const app = useAppConfig() as AppConfigInput
const navbar = ref(null)
const showDrawer = useState<boolean>('navbar.showDrawer', () => false)
const showOptions = useState<boolean>('navbar.showOptions', () => false)

// lifecycle
let timer: NodeJS.Timer
onMounted(() => {
  if (!navbar.value) return

  // scroll
  const { onScroll } = useSticky(navbar.value, 0)
  setTimeout(() => onScroll(), 50)

  // on show on mobile
  setInterval(() => {
    // must in mobile
    const minW = 1024
    if (window.innerWidth < minW) {
      updateDrawerOptions()
    }
  }, 100)
})
onBeforeUnmount(() => {
  if (timer) clearInterval(timer)
})

// methods
const updateDrawerOptions = () => {
  // drawer
  if (showDrawer.value || showOptions.value) {
    document.body.classList.add('overflow-hidden')
  } else {
    document.body.classList.remove('overflow-hidden')
  }
}
const toggleDrawer = () => (showDrawer.value = !showDrawer.value)
const toggleOptions = (show?: boolean) => {
  if (show) {
    showOptions.value = show
  } else {
    showOptions.value = !showOptions.value
  }
}
</script>

<template>
  <div
    ref="navbar"
    class="border-b flex-none bg-white/[0.5] border-gray-900/10 w-full transition-colors top-0 z-40 duration-300 backdrop-filter backdrop-blur-md lg:z-50 dark:bg-slate-900/[0.5] dark:border-gray-50/[0.2]"
  >
    <div id="navbar-banner" class="banner">
      <slot name="banner" />
    </div>
    <div class="mx-auto w-full max-w-8xl">
      <div class="mx-4 py-3 lg:mx-0 lg:px-8">
        <div class="flex relative items-center">
          <!-- drawer:toggle -->
          <div
            v-if="$slots['drawer']"
            class="flex mr-2 items-center self-center justify-center lg:hidden"
          >
            <button
              class="flex items-center focus:outline-none"
              aria-label="Toggle Drawer Menu"
              @click="toggleDrawer()"
            >
              <span
                class="flex text-lg text-gray-600 items-center dark:text-gray-300"
                aria-hidden="true"
              >
                <IconUil:bars v-if="!showDrawer" />
                <IconUil:times v-else />
              </span>
            </button>
          </div>
          <!-- title -->
          <slot name="title">
            <NuxtLink
              tag="a"
              class="flex-none font-bold mr-3 text-md text-gray-900 w-50 overflow-hidden dark:text-gray-200"
              :to="{ name: 'index' }"
            >
              <span class="sr-only">home</span>
              <span class="flex items-center">
                <img
                  class="h-10 mr-4 inline-block"
                  src="~assets/images/logo.svg"
                  alt="LOGO"
                />
              </span>
            </NuxtLink>
          </slot>
          <!-- menu -->
          <slot name="menu" />
          <!-- options:toggle -->
          <div
            v-if="$slots['options']"
            class="flex flex-1 justify-end lg:hidden"
          >
            <button
              class="flex items-center focus:outline-none"
              aria-label="Toggle Options Menu"
              @click="toggleOptions()"
            >
              <span
                class="flex text-sm text-gray-600 items-center dark:text-gray-300"
                aria-hidden="true"
              >
                <icon-fa-solid:ellipsis-v />
              </span>
            </button>
          </div>
        </div>
      </div>
    </div>
    <ClientOnly>
      <Teleport to="#app-after">
        <!-- drawer -->
        <Transition name="slide-fade-from-up" mode="out-in">
          <div
            v-if="showDrawer && $slots['drawer']"
            class="flex flex-col h-screen bg-gray-100 w-screen pt-12 top-0 left-0 z-30 fixed lg:hidden dark:bg-slate-800"
          >
            <div class="flex flex-col flex-1 relative overflow-y-auto">
              <slot name="drawer" :toggle-drawer="toggleDrawer" />
            </div>
          </div>
        </Transition>

        <!-- options -->
        <div v-if="showOptions && $slots['options']">
          <slot
            name="options"
            :toggle-options="toggleOptions"
            :show-options="showOptions"
          />
        </div>
      </Teleport>
    </ClientOnly>
  </div>
</template>

<style lang="scss">
.slide-fade-from-up-enter-active {
  transition: all 0.3s ease-out;
}
.slide-fade-from-up-leave-active {
  transition: all 0.3s cubic-bezier(1, 0.5, 0.8, 1);
}
.slide-fade-from-up-enter-from,
.slide-fade-from-up-leave-to {
  transform: translateY(-20px);
  opacity: 0;
}

a.router-link-active {
  font-weight: bold;
}
a.router-link-exact-active {
  color: theme('colors.slate.900');
}
html.dark {
  a.router-link-exact-active {
    color: theme('colors.white');
  }
}
</style>
