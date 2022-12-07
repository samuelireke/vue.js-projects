<script setup>
  import SideBar from "./components/SideBar.vue"
  import ImageGallery from "./components/ImageGallery.vue"
  import {ref} from "vue"

  const isWithColour = ref(true)

  const onSelectOption = (isColour) => {
    isWithColour.value = isColour
  }
</script>

<template>
  <v-app>
    <!-- sidebar component -->
    <SideBar @selectOption="onSelectOption"/> 
    <v-main>
      <!-- cards -->
      <ImageGallery 
        :isWithColour="isWithColour" />
    </v-main>
  </v-app>
</template>