<script setup lang="ts">
const { t, availableLocales, locale } = useI18n()

const toggleLocales = () => {
  // change to some real logic
  const locales = availableLocales
  locale.value = locales[(locales.indexOf(locale.value) + 1) % locales.length]
}
</script>

<template>
  <div class=" w-full items-center justify-center py-4 bg-gray-200">
    <div class="justify-center flex space-x-6 py-4">
      <img src="/svg/instagram-fill.svg" class="h-6 w-6 cursor-pointer">
      <img src="/svg/pinterest-alt.svg" class="h-6 w-6 cursor-pointer">
      <img src="/svg/facebook.svg" class="h-6 w-6 cursor-pointer">
    </div>
    <div class="text-sm text-gray-600">
      ©2022 COPYRIGHT Sea Zaphryne Photography
    </div>
  </div>
</template>
