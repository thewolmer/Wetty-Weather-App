<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Logoicon from './components/icons/Logoicon.vue'

</script>

<template>
  <header class="flex justify-center">
      <Logoicon />
  </header>

  <RouterView />
</template>


