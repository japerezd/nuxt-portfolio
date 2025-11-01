<template>
<div class="flex space-x-2 items-center">
  <div class="text-gray-500 text-xs" v-if="showNextModeLabel">Change to {{ nextMode }}</div>
  <button @click="toggleMode" @mouseover="showNextModeLabel = true" @mouseout="showNextModeLabel = false" class="hover:bg-gray-200 dark:hover:bg-gray-600 px-2 py-1 text-gray-100">{{ nextModeIcon }}</button>
</div>
</template>

<script setup>
const showNextModeLabel = ref(false)
const colorMode = useColorMode();

const modes = [
  'system',
  'light',
  'dark'
]

const nextModeIcons = {
  system: '🌓',
  light: '🌕',
  dark: '🌑'
}

const nextMode = computed(() => {
  const currentModeIndex = modes.indexOf(colorMode.preference)
  let nextModeIndex = null

  if (currentModeIndex === modes.length - 1) {
    nextModeIndex = 0
  } else {
    nextModeIndex = currentModeIndex + 1
  }

  return modes[nextModeIndex]
})

const nextModeIcon = computed(() => nextModeIcons[nextMode.value])

const toggleMode = () => colorMode.preference = nextMode.value
</script>