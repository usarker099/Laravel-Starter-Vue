<template>
  <AppLayout title="Roles">
    <div class="p-6">
      <div class="flex justify-between items-center mb-6">
        <h1 class="text-2xl font-bold">Roles</h1>
        <Link href="/roles/create" class="btn btn-primary">Create Role</Link>
      </div>

      <div class="overflow-x-auto">
        <table class="table w-full">
          <thead>
            <tr>
              <th>ID</th>
              <th>Name</th>
              <th>Guard Name</th>
              <th>Permissions Count</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="role in roles.data" :key="role.id">
              <td>{{ role.id }}</td>
              <td>{{ role.name }}</td>
              <td>{{ role.guard_name }}</td>
              <td>{{ role.permissions?.length || 0 }}</td>
              <td>
                <Link :href="`/roles/${role.id}/edit`" class="btn btn-sm btn-info mr-2">Edit</Link>
                <button @click="deleteRole(role.id)" class="btn btn-sm btn-error">Delete</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>

      <div class="mt-4">
        <Pagination :links="roles.links" />
      </div>
    </div>
  </AppLayout>
</template>

<script setup>
import { Link } from '@inertiajs/vue3'
import AppLayout from '@/Layouts/AppLayout.vue'
import Pagination from '@/Components/Pagination.vue'
import { router } from '@inertiajs/vue3'

const props = defineProps({
  roles: Object
})

const { delete: destroy } = router

const deleteRole = (id) => {
  if (confirm('Are you sure?')) {
    destroy(`/roles/${id}`)
  }
}
</script>