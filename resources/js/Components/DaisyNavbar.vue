<script setup>
import { ref } from 'vue'
import { Link, router, usePage } from '@inertiajs/vue3'
import ThemeSwitcher from './ThemeSwitcher.vue'

const { props } = usePage()
const showUserDropdown = ref(false)

const logout = () => {
    router.post(route('logout'))
}

const isSuperAdmin = () => {
    return props.auth.roles.includes('Super_Admin')
}
</script>

<template>
  <div class="navbar bg-base-100 shadow-sm px-4">
    <div class="navbar-start">
      <div class="me-2">
        <label for="drawer-toggle" class="btn btn-ghost btn-circle lg:hidden">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h7" />
          </svg>
        </label>
      </div>

      <Link href="/dashboard" class="btn btn-ghost text-xl ms-2">MyApp</Link>
    </div>

    <div class="navbar-center hidden lg:flex">
      <Link href="/dashboard" class="btn btn-ghost">Dashboard</Link>
      <Link href="/dashboard2" class="btn btn-ghost">Dashboard2</Link>
    </div>

    <div class="navbar-end">
      <div class="me-2 text-xs">
        <ThemeSwitcher />
      </div>

      <div class="dropdown dropdown-end">
        <label tabindex="0" class="btn btn-ghost btn-circle avatar" @click="showUserDropdown = !showUserDropdown">
          <div class="w-10 rounded-full">
            <img :src="$page.props.auth.user.profile_photo_url" :alt="$page.props.auth.user.name" />
          </div>
        </label>
        
        <ul tabindex="0" class="menu dropdown-content bg-base-100 rounded-box w-52 p-2 shadow mt-3 z-50"
            :class="{ 'dropdown-open': showUserDropdown }"
            @click="showUserDropdown = false">
          <li class="menu-title">
            <span>{{ $page.props.auth.user.name }}</span>
          </li>

          <li><Link :href="route('profile.show')">Profile</Link></li>
          <li v-if="$page.props.jetstream.hasApiFeatures"><Link :href="route('api-tokens.index')">API Tokens</Link></li>
          <li v-if="isSuperAdmin()">
            <Link :href="route('roles.index')">Roles</Link>
          </li>
          <li v-if="isSuperAdmin()">
            <Link :href="route('permissions.index')">Permissions</Link>
          </li>
          <li v-if="isSuperAdmin()">
            <Link :href="route('users.index')">Users</Link>
          </li>
          <li>
            <button class="text-left w-full" @click="logout">Log Out</button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>