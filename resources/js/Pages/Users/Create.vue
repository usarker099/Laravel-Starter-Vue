<template>
  <AppLayout title="Create User">
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

        <div class="form-control mb-4">
          <label class="label">
            <span class="label-text">Email</span>
          </label>
          <input v-model="form.email" type="email" class="input input-bordered w-full" required />
          <div v-if="form.errors.email" class="label">
            <span class="label-text-alt text-error">{{ form.errors.email }}</span>
          </div>
        </div>

        <div class="form-control mb-4">
          <label class="label">
            <span class="label-text">Password</span>
          </label>
          <input v-model="form.password" type="password" class="input input-bordered w-full" required />
          <div v-if="form.errors.password" class="label">
            <span class="label-text-alt text-error">{{ form.errors.password }}</span>
          </div>
        </div>

        <div class="form-control mb-4">
          <label class="label">
            <span class="label-text">Confirm Password</span>
          </label>
          <input v-model="form.password_confirmation" type="password" class="input input-bordered w-full" required />
        </div>

        <div class="form-control mb-6">
          <label class="label">
            <span class="label-text">Roles</span>
          </label>
          <select v-model="form.roles" multiple class="select select-bordered w-full" size="5">
            <option v-for="role in roles" :key="role.id" :value="role.id">
              {{ role.name }}
            </option>
          </select>
          <div v-if="form.errors.roles" class="label">
            <span class="label-text-alt text-error">{{ form.errors.roles }}</span>
          </div>
        </div>

        <div class="flex justify-end space-x-2">
          <Link href="/users" class="btn btn-ghost">Cancel</Link>
          <button type="submit" class="btn btn-primary" :disabled="form.processing">Create</button>
        </div>
      </form>
    </div>
  </AppLayout>
</template>

<script setup>
import { Link, useForm } from '@inertiajs/vue3'
import AppLayout from '@/Layouts/AppLayout.vue'

const props = defineProps({
  roles: Array
})

const form = useForm({
  name: '',
  email: '',
  password: '',
  password_confirmation: '',
  roles: []
})

const submit = () => {
  form.post('/users')
}
</script>