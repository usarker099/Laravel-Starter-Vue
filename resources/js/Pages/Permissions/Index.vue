<template>
    <AppLayout title="Permissions">
      <div class="p-6">
        <div class="flex justify-between items-center mb-6">
          <h1 class="text-2xl font-bold">Permissions</h1>
          <Link href="/permissions/create" class="btn btn-primary">Create Permission</Link>
        </div>
  
        <div class="overflow-x-auto">
          <table class="table w-full">
            <thead>
              <tr>
                <th>ID</th>
                <th>Name</th>
                <th>Guard Name</th>
                <th>Actions</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="permission in permissions.data" :key="permission.id">
                <td>{{ permission.id }}</td>
                <td>{{ permission.name }}</td>
                <td>{{ permission.guard_name }}</td>
                <td>
                  <Link :href="`/permissions/${permission.id}/edit`" class="btn btn-sm btn-info mr-2">Edit</Link>
                  <button @click="deletePermission(permission.id)" class="btn btn-sm btn-error">Delete</button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
  
        <div class="mt-4">
          <Pagination :links="permissions.links" />
        </div>
      </div>
    </AppLayout>
  </template>
  
  <script setup>
  import { Link } from '@inertiajs/vue3'
  import AppLayout from '@/Layouts/AppLayout.vue'
  import Pagination from '@/Components/Pagination.vue'
  import { router } from '@inertiajs/vue3'
  import { useForm } from '@inertiajs/vue3'
  
  const props = defineProps({
    permissions: Object
  })
  
  const { delete: destroy } = router
  
  const deletePermission = (id) => {
    if (confirm('Are you sure?')) {
      destroy(`/permissions/${id}`)
    }
  }
  </script>