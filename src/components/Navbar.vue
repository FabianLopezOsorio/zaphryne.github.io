<script setup lang="ts">
const { t, availableLocales, locale } = useI18n()

const toggleLocales = () => {
  const locales = availableLocales
  locale.value = locales[(locales.indexOf(locale.value) + 1) % locales.length]
}
const scrolled = ref(true)
const mobileNavbar = ref(false)

const handleScroll = () => {
  scrolled.value = window.scrollY === 0
}
onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})
</script>

<template>
  <nav class=" relative">
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
      class="sm:(!hidden absolute) flex bg-gray-200 py-4 px-5 bg-opacity-60 fixed w-full top-0 z-10 fle  font-bright items-center justify-between"
    >
      <RouterLink class="icon-btn text-left  font-brush text-3xl block" to="/">
        <div>
          Sea Zaphryne
        </div>
        <div>
          Photography
        </div>
      </RouterLink>
      <img v-if="!mobileNavbar" src="/svg/navicon.svg" class="h-10 w-10 cursor-pointer" alt="" @click="mobileNavbar = true">
      <img v-else src="/svg/close.svg" class="h-10 w-10 cursor-pointer" alt="" @click="mobileNavbar = false">
    </div>
    <!-- :class="{ '!-right-1/1': !mobileNavbar }" -->
    <div :class=" !mobileNavbar ? 'scale-x-0' : 'scale-x-110' " class="fixed transform transition-all duration-300 sm:!hidden top-26 w-full h-100vh z-100 p-5 font-bright bg-gray-200 bg-opacity-80">
      <div class="grid grid-cols-1 space-y-2">
        <RouterLink class="icon-btn mx-2 md:text-5xl text-4xl" to="/">
          Home
        </RouterLink>

        <RouterLink class="icon-btn mx-2 md:text-5xl text-4xl" to="/">
          Galery
        </RouterLink>
        <RouterLink class="icon-btn mx-2 md:text-5xl text-4xl" to="/about">
          About us
        </RouterLink>

        <RouterLink class="icon-btn mx-2 md:text-5xl text-4xl" to="/">
          Contact
        </RouterLink>
      </div>
    </div>
  </nav>
</template>
