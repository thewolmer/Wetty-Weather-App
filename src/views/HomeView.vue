<script setup>
  import FooterVue from '../components/Footer.vue';
  import { defineAsyncComponent } from 'vue';
  const AsyncShowData = defineAsyncComponent(() => import('../components/ShowData.vue'))
  </script>

<template>
  <main class="items-center bg-neutral-900 h-screen text-center place-items-center">
    
    
<Suspense>
  <template #default>
<AsyncShowData />
</template>
  <template #fallback>
  <div class="border border-neutral-500 shadow rounded-md p-8 mt-6 max-w-sm w-full mx-auto">
  <div class="animate-pulse flex space-x-4">
    <div class="flex-1 space-y-6 py-1">
      <div class="h-2 bg-neutral-600 rounded"></div>
      <div class="space-y-3">
        <div class="grid grid-cols-3 gap-4">
          <div class="h-2 bg-neutral-600 rounded col-span-2"></div>
          <div class="h-2 bg-neutral-600 rounded col-span-1"></div>
        </div>
        <div class="h-2 bg-neutral-600 rounded"></div>
      </div>
    </div>
  </div>
</div>
</template>
</Suspense>
  
<FooterVue />
  </main>
  </template>
  


