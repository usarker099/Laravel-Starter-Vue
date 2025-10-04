<script setup>
import { computed } from 'vue';
import { Link } from '@inertiajs/vue3';

const props = defineProps({
    active: Boolean,
    href: String,
    as: String,
});

const classes = computed(() => {
    return props.active
        ? 'block w-full ps-3 pe-4 py-2 border-l-4 border-primary text-base font-medium text-primary-focus bg-primary/10 rounded-r-lg transition duration-150 ease-in-out'
        : 'block w-full ps-3 pe-4 py-2 border-l-4 border-transparent text-base font-medium text-base-content/70 hover:text-primary hover:bg-primary/10 hover:border-primary rounded-r-lg transition duration-150 ease-in-out';
});
</script>

<template>
    <div>
        <button v-if="as === 'button'" :class="classes">
            <slot />
        </button>

        <a v-else-if="as === 'a'" :class="classes" :href="href">
            <slot />
        </a>

        <Link v-else :href="href" :class="classes">
            <slot />
        </Link>
    </div>
</template>
