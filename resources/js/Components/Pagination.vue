<template>

    <div class="join mt-4">
      <button
        v-for="link in links"
        :key="link.url"
        class="join-item btn"
        :class="[
          link.active && 'btn-active',
          !link.url && 'btn-disabled cursor-not-allowed'
        ]"
        @click="onClick(link)"
      >
        {{ link.label }}
      </button>
    </div>
  </template>
  
  <script setup>
  import { router } from '@inertiajs/vue3'
  
  const props = defineProps({
    links: Array
  })
  
  const onClick = (link) => {
    if (link.url) {
      router.get(link.url, {}, {
        preserveState: true,
        preserveScroll: true,
      })
    }
  }
  </script>