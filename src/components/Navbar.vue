<script setup lang="ts">
const { t, availableLocales, locale } = useI18n()

const toggleLocales = () => {
  const locales = availableLocales
  locale.value = locales[(locales.indexOf(locale.value) + 1) % locales.length]
}
const scrolled = ref(true)
const handleScroll = () => {
  scrolled.value = window.scrollY === 0
}
onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})
</script>

<template>
  <nav text-xl class=" bg-gray-200 py-4 flex bg-opacity-60 absolute w-full top-0 z-10  font-bright items-center justify-around">
    <div>
      <RouterLink class="icon-btn mx-2 text-5xl" to="/">
        Home
      </RouterLink>

      <RouterLink class="icon-btn mx-2 text-5xl" to="/">
        Galery
      </RouterLink>
    </div>

    <RouterLink :class="{ '!text-5xl': !scrolled }" class="icon-btn transition-all duration-300  font-brush text-7xl block" to="/">
      <div>
        Sea Zaphryne
      </div>
      <div :class="{ '!text-lg': !scrolled }" class="transition-all duration-300 text-2xl">
        Photography
      </div>
    </RouterLink>
    <div>
      <RouterLink class="icon-btn mx-2 text-5xl" to="/about">
        About us
      </RouterLink>

      <RouterLink class="icon-btn mx-2 text-5xl" to="/">
        Contact
      </RouterLink>
    </div>
  </nav>
</template>
