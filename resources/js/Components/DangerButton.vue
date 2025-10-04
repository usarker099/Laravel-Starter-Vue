<script setup>
defineProps({
    type: {
        type: String,
        default: 'button',
    },
});
</script>

<template>
  <button 
    :type="type" 
    class="btn btn-primary px-4 py-2 rounded-md text-xs uppercase tracking-widest transition"
  >
    <slot />
  </button>
</template>
