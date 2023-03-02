<template>
  <div>
    <slot name="app-before" />
    <div id="app-before"></div>
    <div class="flex flex-col min-h-screen">
      <slot name="header">
        <PageNavbar />
      </slot>
      <div class="flex flex-col flex-1 w-full">
        <div
          class="flex flex-col h-full mx-auto flex-1 w-full max-w-8xl relative"
        >
          <slot />
        </div>
      </div>
      <slot name="footer">
        <PageFooter class="z-9" />
      </slot>
    </div>
    <slot name="app-after" />
    <div id="app-after"></div>
  </div>
</template>
