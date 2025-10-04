<template>
  <AppLayout title="Users">
    <div class="p-6">
      <div class="flex justify-between items-center mb-6">
        <h1 class="text-2xl font-bold">Users</h1>
        <Link href="/users/create" class="btn btn-primary">Create User</Link>
      </div>

      <div class="overflow-x-auto">
        <table class="table w-full">
          <thead>
            <tr>
              <th>ID</th>
              <th>Name</th>
              <th>Email</th>
              <th>Roles</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="user in users.data" :key="user.id">
              <td>{{ user.id }}</td>
              <td>{{ user.name }}</td>
              <td>{{ user.email }}</td>
              <td>
                <span v-if="user.roles && user.roles.length" class="badge badge-secondary mr-1" v-for="role in user.roles" :key="role.id">
                  {{ role.name }}
                </span>
                <span v-else class="text-sm text-gray-500">No roles</span>
              </td>
              <td>
                <Link :href="`/users/${user.id}/edit`" class="btn btn-sm btn-info mr-2">Edit</Link>
                <button @click="deleteUser(user.id)" class="btn btn-sm btn-error">Delete</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>

      <div class="mt-4">
        <Pagination :links="users.links" />
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
  users: Object
})

const { delete: destroy } = router

const deleteUser = (id) => {
  if (confirm('Are you sure?')) {
    destroy(`/users/${id}`)
  }
}
</script>