<script setup>
import { Head, Link } from '@inertiajs/vue3'

defineProps({
  canLogin: Boolean,
  canRegister: Boolean,
  laravelVersion: {
    type: String,
    required: true,
  },
  phpVersion: {
    type: String,
    required: true,
  },
})

function handleImageError() {
  document.getElementById('screenshot-container')?.classList.add('!hidden')
  document.getElementById('docs-card')?.classList.add('!row-span-1')
  document.getElementById('docs-card-content')?.classList.add('!flex-row')
  document.getElementById('background')?.classList.add('!hidden')
}
</script>

<template>
  <Head title="Welcome" />

  <div class="min-h-screen flex flex-col bg-gray-50 dark:bg-black text-black/70 dark:text-white/70">

    <!-- Header -->
    <header class="flex justify-between items-center w-full px-6 py-4">
      <div>
        <h1 class="text-lg font-bold"></h1>
      </div>

      <nav v-if="canLogin" class="flex space-x-4">
        <Link
          v-if="$page.props.auth.user"
          :href="route('dashboard')"
          class="px-3 py-2 text-sm font-medium rounded-md hover:bg-gray-200 dark:hover:bg-gray-800"
        >
          Dashboard
        </Link>

        <template v-else>
          <Link
            :href="route('login')"
            class="px-3 py-2 text-sm font-medium rounded-md hover:bg-gray-200 dark:hover:bg-gray-800"
          >
            Log in
          </Link>
          <Link
            v-if="canRegister"
            :href="route('register')"
            class="px-3 py-2 text-sm font-medium rounded-md hover:bg-gray-200 dark:hover:bg-gray-800"
          >
            Register
          </Link>
        </template>
      </nav>
    </header>

    <!-- Main Content (Centered) -->
    <main class="flex flex-1 flex-col items-center justify-center text-center px-6">


      <h2 class="text-3xl font-bold mt-6">Hello </h2>



    </main>

    <!-- Footer -->
    <footer class="py-6 text-center text-sm text-gray-500 dark:text-gray-400">
      Laravel v{{ laravelVersion }} (PHP v{{ phpVersion }})
    </footer>
  </div>
</template>
