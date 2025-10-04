<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import Welcome from '@/Components/Welcome.vue';
import ThemeSwitcher from '@/Components/ThemeSwitcher.vue';
</script>

<template>
    <AppLayout title="Dashboard">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Dashboard
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="overflow-hidden shadow-xl sm:rounded-lg bg-base-100 text-base-content">

                    <!-- Welcome Section -->
                    <div class="p-6">
                        <h1 class="text-2xl font-bold mt-4">Welcome</h1>
                        <Welcome />
                    </div>

                </div>
            </div>
        </div>
    </AppLayout>
</template>
