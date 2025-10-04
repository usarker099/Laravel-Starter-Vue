<template>
    <AppLayout title="Edit Permission">
      <div class="p-6 max-w-md">
        <form @submit.prevent="submit">
          <div class="form-control mb-4">
            <label class="label">
              <span class="label-text">Name</span>
            </label>
            <input v-model="form.name" type="text" class="input input-bordered w-full" required />
            <div v-if="form.errors.name" class="label">
              <span class="label-text-alt text-error">{{ form.errors.name }}</span>
            </div>
          </div>
  
          <div class="form-control mb-6">
            <label class="label">
              <span class="label-text">Guard Name</span>
            </label>
            <input v-model="form.guard_name" type="text" class="input input-bordered w-full" required />
            <div v-if="form.errors.guard_name" class="label">
              <span class="label-text-alt text-error">{{ form.errors.guard_name }}</span>
            </div>
          </div>
  
          <div class="flex justify-end space-x-2">
            <Link :href="`/permissions`" class="btn btn-ghost">Cancel</Link>
            <button type="submit" class="btn btn-primary" :disabled="form.processing">Update</button>
          </div>
        </form>
      </div>
    </AppLayout>
  </template>
  
  <script setup>
  import { Link, useForm } from '@inertiajs/vue3'
  import AppLayout from '@/Layouts/AppLayout.vue'
  
  const props = defineProps({
    permission: Object
  })
  
  const form = useForm({
    name: props.permission.name,
    guard_name: props.permission.guard_name
  })
  
  const submit = () => {
    form.put(`/permissions/${props.permission.id}`)
  }
  </script>