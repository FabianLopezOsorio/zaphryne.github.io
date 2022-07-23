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
  <nav class=" ">
    <div
      class="hidden sm:(flex bg-gray-200 py-4  bg-opacity-60 absolute w-full top-0 z-10  font-bright items-center justify-around)"
    >
      <div>
        <RouterLink class="icon-btn mx-2 md:text-5xl text-3xl" to="/">
          Home
        </RouterLink>

        <RouterLink class="icon-btn mx-2 md:text-5xl text-3xl" to="/">
          Galery
        </RouterLink>
      </div>

      <RouterLink
        :class="{ '!text-5xl': !scrolled }"
        class="icon-btn transition-all duration-300  font-brush text-7xl block" to="/"
      >
        <div>
          Sea Zaphryne
        </div>
        <div :class="{ '!text-lg': !scrolled }" class="transition-all duration-300 text-2xl">
          Photography
        </div>
      </RouterLink>
      <div>
        <RouterLink class="icon-btn mx-2 md:text-5xl text-3xl" to="/about">
          About us
        </RouterLink>

        <RouterLink class="icon-btn mx-2 md:text-5xl text-3xl" to="/">
          Contact
        </RouterLink>
      </div>
    </div>
    <div
      class="sm:!hidden flex bg-gray-200 py-4 px-5 bg-opacity-60 absolute w-full top-0 z-10 fle  font-bright items-center justify-between"
    >
      <RouterLink class="icon-btn text-left  font-brush text-3xl block" to="/">
        <div>
          Sea Zaphryne
        </div>
        <div>
          Photography
        </div>
      </RouterLink>
      <img src="/svg/navicon.svg" class="h-10 w-10 cursor-pointer" alt="">
    </div>
  </nav>
</template>
