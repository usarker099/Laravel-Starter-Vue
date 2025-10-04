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
        class="inline-flex items-center px-4 py-2 bg-base-100 border border-base-300 rounded-md font-semibold text-xs text-base-content uppercase tracking-widest shadow-sm hover:bg-base-200 focus:outline-none focus:ring focus:ring-primary focus:ring-offset-2 disabled:opacity-50 transition ease-in-out duration-150"
    >
        <slot />
    </button>
</template>
