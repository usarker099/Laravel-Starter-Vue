<script setup>
import { ref, watchEffect } from 'vue';
import { usePage } from '@inertiajs/vue3';

const page = usePage();
const show = ref(true);
const style = ref('success');
const message = ref('');

watchEffect(() => {
    style.value = page.props.jetstream.flash?.bannerStyle || 'success';
    message.value = page.props.jetstream.flash?.banner || '';
    show.value = true;
});

function styleClass(style) {
    switch (style) {
        case 'success':
            return 'alert-success';
        case 'danger':
            return 'alert-error';
        case 'warning':
            return 'alert-warning';
        case 'info':
            return 'alert-info';
        default:
            return 'alert';
    }
}
</script>

<template>
  <div>
    <div v-if="show && message">
      <div :class="['alert', styleClass(style)]">
        <div class="flex-1">
          <svg v-if="style=='success'" class="size-5 flex-shrink-0" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
          </svg>

          <svg v-if="style=='danger'" class="size-5 flex-shrink-0" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" d="M12 9v3.75m-9.303 3.376c-.866 1.5.217 3.374 1.948 3.374h14.71c1.73 0 2.813-1.874 1.948-3.374L13.949 3.378c-.866-1.5-3.032-1.5-3.898 0L2.697 16.126zM12 15.75h.007v.008H12v-.008z" />
          </svg>

          <span class="ms-3 font-medium text-base-content truncate">
            {{ message }}
          </span>
        </div>

        <div class="flex-none">
          <button type="button" class="btn btn-ghost btn-sm" @click.prevent="show=false">
            ✕
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
