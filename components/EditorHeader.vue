<template>
  <div class="h-20 w-full border-b border-[#e2e8f0] bg-white px-4 py-2">
    <div class="flex h-full items-center justify-between">
      <div class="flex items-center">
        <a href="https://www.prisma.io" target="_blank"><img src="/svg/logo.svg" alt="logo" /></a>
        <a href="/editor" class="mt-1 transition-transform duration-[0.18s] ease-[ease-out] hover:-translate-y-0.5">
          <span class="font-inter -ml-3 cursor-pointer text-[22px] leading-[100%] font-medium text-[#2d3748] not-italic">/viewer</span>
        </a>
      </div>
      <div class="flex gap-4">
        <a href="https://github.com/Jofa8/prismaviewer" target="_blank" class="flex items-center">
          <Icon name="mdi:github" style="width: 28px; height: 28px" class="text-[#2d3748]" />
        </a>
        <Icon
          :name="fullScreen ? 'ic:baseline-fullscreen-exit' : 'ic:baseline-fullscreen'"
          style="width: 28px; height: 28px"
          class="cursor-pointer text-[#2d3748]"
          @click="toggleFullscreen"
        />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const fullScreen = ref(false)

const toggleFullscreen = () => {
  if (!document.fullscreenElement) {
    document.documentElement.requestFullscreen()
    fullScreen.value = true
  } else {
    document.exitFullscreen()
    fullScreen.value = false
  }
}
</script>
