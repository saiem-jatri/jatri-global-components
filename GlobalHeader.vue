<script setup>
import { ref } from "vue";
const sidebarOpen = ref(false)
const closeModal = () => {
  let getBody = document.getElementsByTagName('body')[0];
  sidebarOpen.value = false
  getBody.style.overflow = 'auto';
}
const toggleModal = () => {
  sidebarOpen.value = true;
  let getBody = document.getElementsByTagName('body')[0];
  if (sidebarOpen.value) {
    getBody.style.overflow = 'hidden';
  }
}
</script>
<template>
  <div class="sticky top-0 left-0 z-[999] w-full bg-white border-b border-[#EDEDED]">
    <div class="custom-container">
      <div class="flex justify-between items-center py-[14px] lg:py-4">
        <div class="flex justify-between md:justify-start items-center gap-x-2 md:gap-x-8 w-full">
          <nuxt-link :to="('/')"><img class="w-[50px] h-[26px] lg:h-9 lg:w-[74px]" src="~/assets/images/header/jatri-logo.svg" alt="jatri logo"></nuxt-link>
          <div class="bg-[#FEF2F0] rounded-full p-1">
            <div class="flex gap-x-1 lg:gap-x-2 justify-center items-center">
              <div class="py-1 px-2 lg:px-3 rounded-full activeMenu">
                <!--If you need active menu use invert in img class and use activeMenu class in parent div-->
                <a href="https://rental.jatri.co/" target="_blank" class="linkItem">
                  <img class="invert w-3 lg:w-5" src="~/assets/images/header/car-svg.svg" alt="">
                  <span class="text-sm lg:text-base text-dark">Rental</span>
                </a>
              </div>
              <div class="py-1 px-2 lg:px-3 rounded-full">
                <a href="https://ticket.jatri.co/" class="linkItem">
                  <img class="w-3 lg:w-5" src="~/assets/images/header/bus_2.svg" alt="">
                  <span class="text-sm lg:text-base text-dark">Bus</span>
                </a>
              </div>
              <div class="py-1 px-2 lg:px-3 rounded-full">
                <a href="https://ticket.jatri.co/launch" class="linkItem">
                  <img class="w-3 lg:w-5" src="~/assets/images/header/Ship.svg" alt="">
                  <span class="text-sm lg:text-base text-dark">Launch</span>
                </a>
              </div>
            </div>
          </div>
        </div>

        <div class="flex items-center md:hidden ml-4">
          <button @click="toggleModal"><img class="w-6 h-6" src="~/assets/images/header/3bar-icon.svg" alt=""></button>
        </div>

        <div v-if="sidebarOpen" class="bg-white absolute inset-y-0 right-0 -translate-x-[300px] slide" 
          :class="sidebarOpen ? 'absolute z-50 translate-x-0 transition delay-300 duration-300' : ''">
          <div class="h-screen w-[300px] bg-white gap-y-10">
            <div class="flex justify-between items-center border-b border-[#EDEDED] px-4 py-5">
              <p class="font-medium text-sm text-black uppercase">menu</p>
              <button @click="closeModal" class=""><img src="~/assets/images/header/cross-icon.svg" alt="X"></button>
            </div>
            <div class="flex flex-col px-2">
              <!--Place your all menu items here-->
            </div>
          </div>
        </div>
        <div v-if="sidebarOpen" @click="closeModal"
          class="fixed inset-0 z-30 bg-black bg-opacity-30 h-full w-full cursor-default transition duration-300 ease-in-out">
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.linkItem{
  @apply flex justify-center items-center gap-x-1 lg:gap-x-2 text-xs lg:text-base font-normal
}
.slide {
  @apply absolute animate-[slide_0.5s_forwards] -right-2/4;
}
.activeMenu{
  @apply bg-[#f04935] text-white
}
@keyframes slide {
  100% {
    right: 0;
  }
}
</style>