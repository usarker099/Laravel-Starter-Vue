<script setup>
import { Head, usePage, router } from '@inertiajs/vue3'
import DaisyNavbar from '@/Components/DaisyNavbar.vue'
import AdminSidebar from '@/Components/AdminSidebar.vue'

defineProps({ title: String })

const navLinks = [
  { label: 'Dashboard', href: route('dashboard') },
  { label: 'Profile', href: route('profile.show') }
]
const page = usePage()
const user = page.props.auth.user
const teams = user.all_teams || []
const currentTeam = user.current_team

const switchTeam = (team) => {
  router.put(route('current-team.update'), { team_id: team.id })
}

const logout = () => {
  router.post(route('logout'))
}
</script>

<template>
    <div class="drawer drawer-mobile">
      <Head :title="title" />
      
      <input id="drawer-toggle" type="checkbox" class="drawer-toggle" />
  
      <div class="drawer-side">
        <label for="drawer-toggle" aria-label="close sidebar" class="drawer-overlay"></label>
        
        <AdminSidebar :items="navLinks" />
      </div>
    <!-- Main Content -->
    <div class="drawer-content flex flex-col min-h-screen bg-base-100">
      <DaisyNavbar
        :brand="'MyApp'"
        :navLinks="navLinks"
        :user="user"
        :hasTeams="!!teams.length"
        :teams="teams"
        :currentTeam="currentTeam"
        :switchTeam="switchTeam"
        :logout="logout"
      />

      <header v-if="$slots.header" class="bg-base-200 shadow-sm">
        <div class="max-w-7xl mx-auto py-4 px-6 sm:px-8">
          <slot name="header" />
        </div>
      </header>

      <main class="flex-1 p-6 sm:p-8">
        <slot />
      </main>
    </div>
  </div>
</template>
