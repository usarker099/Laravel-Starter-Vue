<script setup>
import ThemeSwitcher from '@/Components/ThemeSwitcher.vue'
</script>

<template>
  <div class="p-6 space-y-12">

<div class="p-6 bg-base-100 text-base-content rounded-lg shadow-lg">
  <h1 class="text-2xl font-bold">Theme-aware card</h1>
  <p>This text and background respond to all DaisyUI themes.</p>
  <button class="btn btn-primary mt-2">Button</button>
</div>


    <!-- Typography -->
    <section class="space-y-2">
      <h1 class="text-3xl font-bold text-base-content">Typography</h1>
      <p class="text-base-content">This is a paragraph demonstrating theme-aware text.</p>
      <h2 class="text-2xl font-semibold text-base-content">Subheading</h2>
      <h3 class="text-xl font-medium text-base-content">Sub-subheading</h3>
    </section>

    <!-- Buttons -->
    <section class="space-y-2">
      <h1 class="text-2xl font-bold text-base-content">Buttons</h1>
      <div class="flex flex-wrap gap-2">
        <button class="btn">Default</button>
        <button class="btn btn-primary">Primary</button>
        <button class="btn btn-secondary">Secondary</button>
        <button class="btn btn-accent">Accent</button>
        <button class="btn btn-info">Info</button>
        <button class="btn btn-success">Success</button>
        <button class="btn btn-warning">Warning</button>
        <button class="btn btn-error">Error</button>
        <button class="btn btn-outline">Outline</button>
      </div>
    </section>

    <!-- Inputs -->
    <section class="space-y-2">
      <h1 class="text-2xl font-bold text-base-content">Inputs</h1>
      <input type="text" placeholder="Input text" class="input input-bordered w-full max-w-xs" />
      <textarea class="textarea textarea-bordered w-full max-w-xs" placeholder="Textarea"></textarea>
      <select class="select select-bordered w-full max-w-xs">
        <option disabled selected>Select option</option>
        <option>Option 1</option>
        <option>Option 2</option>
      </select>
    </section>

    <!-- Cards -->
    <section class="space-y-2">
      <h1 class="text-2xl font-bold text-base-content">Cards</h1>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
        <div class="card w-80 bg-base-100 shadow-xl">
          <figure><img src="https://placeimg.com/400/225/arch" alt="Sample" /></figure>
          <div class="card-body">
            <h2 class="card-title text-base-content">Card Title</h2>
            <p class="text-base-content">This card responds to theme changes.</p>
            <div class="card-actions justify-end">
              <button class="btn btn-primary">Action</button>
            </div>
          </div>
        </div>

        <div class="card w-80 bg-primary text-primary-content shadow-xl">
          <div class="card-body">
            <h2 class="card-title">Primary Card</h2>
            <p>Uses primary theme colors</p>
            <div class="card-actions justify-end">
              <button class="btn btn-secondary">Action</button>
            </div>
          </div>
        </div>

        <div class="card w-80 bg-base-200 shadow-xl">
          <div class="card-body">
            <h2 class="card-title text-base-content">Card Example</h2>
            <p class="text-base-content">Base-200 styled card</p>
            <div class="card-actions justify-end">
              <button class="btn btn-accent">Click</button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Alerts -->
    <section class="space-y-2">
      <h1 class="text-2xl font-bold text-base-content">Alerts</h1>
      <div class="alert alert-info">Info Alert</div>
      <div class="alert alert-success">Success Alert</div>
      <div class="alert alert-warning">Warning Alert</div>
      <div class="alert alert-error">Error Alert</div>
    </section>

    <!-- Badges -->
    <section class="space-y-2">
      <h1 class="text-2xl font-bold text-base-content">Badges</h1>
      <div class="flex flex-wrap gap-2">
        <span class="badge">Default</span>
        <span class="badge badge-primary">Primary</span>
        <span class="badge badge-secondary">Secondary</span>
        <span class="badge badge-accent">Accent</span>
        <span class="badge badge-info">Info</span>
        <span class="badge badge-success">Success</span>
        <span class="badge badge-warning">Warning</span>
        <span class="badge badge-error">Error</span>
      </div>
    </section>

    <!-- Table -->
    <section class="space-y-2">
      <h1 class="text-2xl font-bold text-base-content">Table</h1>
      <div class="overflow-x-auto">
        <table class="table w-full">
          <thead>
            <tr>
              <th>#</th>
              <th>Name</th>
              <th>Job</th>
              <th>Status</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <th>1</th>
              <td>John</td>
              <td>Developer</td>
              <td><span class="badge badge-success">Active</span></td>
            </tr>
            <tr>
              <th>2</th>
              <td>Jane</td>
              <td>Designer</td>
              <td><span class="badge badge-warning">Pending</span></td>
            </tr>
            <tr>
              <th>3</th>
              <td>Bob</td>
              <td>Manager</td>
              <td><span class="badge badge-error">Inactive</span></td>
            </tr>
          </tbody>
        </table>
      </div>
    </section>

    <!-- Modal -->
    <section class="space-y-2">
      <h1 class="text-2xl font-bold text-base-content">Modal</h1>
      <label for="my-modal" class="btn modal-button">Open Modal</label>
      <input type="checkbox" id="my-modal" class="modal-toggle" />
      <div class="modal">
        <div class="modal-box">
          <h3 class="font-bold text-lg text-base-content">Modal Example</h3>
          <p class="py-4 text-base-content">This modal responds to theme changes.</p>
          <div class="modal-action">
            <label for="my-modal" class="btn">Close</label>
          </div>
        </div>
      </div>
    </section>

    <!-- Pagination -->
    <section class="space-y-2">
      <h1 class="text-2xl font-bold text-base-content">Pagination</h1>
      <div class="join">
        <button class="btn join-item">«</button>
        <button class="btn join-item">1</button>
        <button class="btn join-item">2</button>
        <button class="btn join-item">3</button>
        <button class="btn join-item">»</button>
      </div>
    </section>

  </div>
</template>
