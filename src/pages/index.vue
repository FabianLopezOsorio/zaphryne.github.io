<script setup lang="ts">
import { Carousel, Navigation, Pagination, Slide } from 'vue3-carousel'
import 'vue3-carousel/dist/carousel.css'

const user = useUserStore()
const name = $ref(user.savedName)
const slides = ['/images/boda1.jpg', '/images/boda2.jpeg', '/images/boda3.jpg']
const router = useRouter()
const { t } = useI18n()
</script>

<template>
  <div>
    <Carousel :autoplay="4500" :wrap-around="true" :pause-autoplay-on-hover="true" class="h-80vh">
      <Slide v-for="slide in slides" :key="slide">
        <div class="carousel__item h-full w-full bg-transparent relative">
          <img class="h-80vh w-full object-cover " :src="slide">
        </div>
      </Slide>
      <template #addons>
        <Navigation />
        <!-- <Pagination /> -->
      </template>
    </Carousel>
  </div>
  <div class="min-h-50vh items-center justify-center p-4 py-8">
    <div class="text-6xl font-brush">
      Sea Zaphryne
    </div>
    <div class="font-baskerville text-4xl">
      Photography Studio
    </div>
    <div class="text-2xl my-8 mx-auto w-min border-teal-600 border-b-2 font-baskerville">
      Services:
    </div>
    <div class="grid-cols-2 font-baskerville grid w-6/10 mx-auto">
      <div class=" justify-self-center space-y-3">
        <div class="flex items-center space-x-2">
          <img src="/svg/check-circle-solid.svg" class="h-6 w-6 text-blue-gray-800">
          <div>Fashion</div>
        </div>
        <div class="flex items-center space-x-2">
          <img src="/svg/check-circle-solid.svg" class="h-6 w-6 text-blue-gray-800">
          <div>Event</div>
        </div>
        <div class="flex items-center space-x-2">
          <img src="/svg/check-circle-solid.svg" class="h-6 w-6 text-blue-gray-800">
          <div>Corporate</div>
        </div>
      </div>
      <div class=" justify-self-center space-y-3">
        <div class="flex items-center space-x-2">
          <img src="/svg/check-circle-solid.svg" class="h-6 w-6 text-blue-gray-800">
          <div>Wedding</div>
        </div>
        <div class="flex items-center space-x-2">
          <img src="/svg/check-circle-solid.svg" class="h-6 w-6 text-blue-gray-800">
          <div>Family</div>
        </div>
        <div class="flex items-center space-x-2">
          <img src="/svg/check-circle-solid.svg" class="h-6 w-6 text-blue-gray-800">
          <div>& Other Services</div>
        </div>
      </div>
    </div>
  </div>
  <div class="bgParallax h-60vh bg-cover">
    <div class="pt-1/8 font-brush text-6xl text-teal-600">
      Browse my collection of high quality, finely detailed photos
    </div>
    <button
      class="font-baskerville  mt-4 py-2 rounded-full bg-transparent border-2 border-teal-600 text-teal-600 hover:(bg-teal-600 bg-opacity-10)"
    >
      Galery
    </button>
  </div>
  <div class="h-50vh" />
</template>

<route lang="yaml">
meta:
  layout: home
</route>

<style scoped>
.carousel__pagination-button {
  margin: 10px !important;
}
</style>
