<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import ThemeSwitcher from '@/Components/ThemeSwitcher.vue';
</script>

<template>
  <AppLayout title="Components Demo">
    <div class="drawer lg:drawer-open min-h-screen">
      <input id="my-drawer-2" type="checkbox" class="drawer-toggle" />
      
      <div class="drawer-content flex flex-col p-4 sm:p-6 lg:p-8 bg-base-200">
        
        <!-- Header -->
        <div class="flex justify-between items-center mb-6 pb-4 border-b border-base-300">

          
          <div class="flex items-center space-x-4">
            <h1 class="text-2xl sm:text-3xl font-bold text-primary">DaisyUI Components Showcase</h1>
         
          </div>
        </div>
        
        <!-- Welcome Section -->
        <Welcome class="mb-8 hidden sm:block" />
        
        <!-- Stats Section -->
        <div class="stats stats-vertical lg:stats-horizontal shadow bg-base-100 mb-8 w-full">
          <div class="stat">
            <div class="stat-figure text-primary">
              <div class="radial-progress text-primary" style="--value:70; --size:3.5rem;">70%</div>
            </div>
            <div class="stat-title">New Users</div>
            <div class="stat-value">31K</div>
            <div class="stat-desc text-primary">↗︎ 400 (22%)</div>
          </div>
          
          <div class="stat">
            <div class="stat-figure text-secondary">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" class="inline-block w-8 h-8 stroke-current"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path></svg>
            </div>
            <div class="stat-title">Revenue</div>
            <div class="stat-value text-secondary">$4,200</div>
            <div class="stat-desc">↓ 200 (5%)</div>
          </div>
          
          <div class="stat">
            <div class="stat-figure">
              <div class="avatar online">
                <div class="w-12 rounded-full">
                  <img src="https://daisyui.com/images/stock/photo-1534528741775-53994a69daeb.jpg" alt="User Avatar" />
                </div>
              </div>
            </div>
            <div class="stat-value">86%</div>
            <div class="stat-title">Tasks Done</div>
            <div class="stat-desc text-accent">31 tasks remaining</div>
          </div>
        </div>
        
        <!-- Main Content Card -->
        <div class="card w-full shadow-xl bg-base-100 p-6 lg:p-8">
          <h2 class="card-title mb-8 text-2xl font-bold">DaisyUI Components Demo</h2>
          
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6 lg:gap-8">
            
            <!-- Avatar & Breadcrumb -->
            <div class="space-y-4">
              <h3 class="text-xl font-bold">Avatar & Breadcrumb</h3>
              <div class="avatar">
                <div class="w-24 rounded-full ring ring-primary ring-offset-base-100 ring-offset-2">
                  <img src="https://daisyui.com/images/stock/photo-1534528741775-53994a69daeb.jpg" alt="User Avatar" />
                </div>
              </div>
              <div class="text-xs breadcrumbs">
                <ul>
                  <li><a>Home</a></li> 
                  <li><a>Documents</a></li> 
                  <li>Add Document</li>
                </ul>
              </div>
            </div>

            <!-- Accordion & Collapse -->
            <div class="space-y-4">
              <h3 class="text-xl font-bold">Accordion & Collapse</h3>
              <div class="collapse collapse-plus bg-base-200">
                <input type="radio" name="my-accordion-3" checked /> 
                <div class="collapse-title text-md font-medium">Click to open me</div>
                <div class="collapse-content"> 
                  <p>Content for the accordion section.</p>
                </div>
              </div>
              <div tabindex="0" class="collapse collapse-arrow border border-base-300 bg-base-200">
                <div class="collapse-title text-md font-medium">Click me for collapse</div>
                <div class="collapse-content"> 
                  <p>Content for the collapse section.</p>
                </div>
              </div>
            </div>
            
            <!-- Inputs: Toggle, Checkbox, Radio -->
            <div class="space-y-4 border p-4 rounded-box">
              <h3 class="text-xl font-bold">Inputs: Toggle, Checkbox, Radio</h3>
              <div class="flex flex-col space-y-3">
                <label class="label cursor-pointer justify-start">
                  <input type="checkbox" class="toggle toggle-primary mr-2" checked />
                  <span class="label-text">Toggle Switch</span>
                </label>
                <div class="form-control">
                  <label class="label cursor-pointer justify-start">
                    <input type="checkbox" checked class="checkbox checkbox-secondary mr-2" />
                    <span class="label-text">Remember me</span>
                  </label>
                </div>
                <div class="form-control">
                  <label class="label cursor-pointer justify-start">
                    <input type="radio" name="radio-10" class="radio checked:bg-red-500 mr-2" checked />
                    <span class="label-text">Option A</span>
                  </label>
                </div>
              </div>
            </div>

            <!-- Progress & Loading -->
            <div class="space-y-4">
              <h3 class="text-xl font-bold">Progress & Loading</h3>
              <progress class="progress progress-warning w-full"></progress>
              <div class="flex items-center space-x-4">
                <span class="loading loading-spinner loading-lg text-success"></span>
                <span class="loading loading-ring loading-md text-error"></span>
              </div>
              <div class="text-center">
                <div class="radial-progress text-info" style="--value:90;">90% Complete</div>
              </div>
            </div>
            
            <!-- Range & Rating -->
            <div class="space-y-4">
              <h3 class="text-xl font-bold">Range & Rating</h3>
              <input type="range" min="0" max="100" value="75" class="range range-primary w-full" />
              <div class="rating rating-sm">
                <input type="radio" name="rating-2" class="mask mask-star-2 bg-orange-400" />
                <input type="radio" name="rating-2" class="mask mask-star-2 bg-orange-400" checked />
                <input type="radio" name="rating-2" class="mask mask-star-2 bg-orange-400" />
                <input type="radio" name="rating-2" class="mask mask-star-2 bg-orange-400" />
                <input type="radio" name="rating-2" class="mask mask-star-2 bg-orange-400" />
              </div>
            </div>

            <!-- Steps & Divider -->
            <div class="space-y-4">
              <h3 class="text-xl font-bold">Steps & Divider</h3>
              <ul class="steps steps-vertical lg:steps-horizontal w-full text-sm">
                <li class="step step-primary">Register</li>
                <li class="step step-primary">Choose plan</li>
                <li class="step">Purchase</li>
                <li class="step">Receive product</li>
              </ul>
              <div class="divider">OR</div>
              <fieldset class="border p-3 rounded-box">
                <legend class="text-lg font-semibold">Fieldset Demo</legend>
                <p class="text-sm">This content is inside a custom-styled fieldset.</p>
              </fieldset>
            </div>
            
            <!-- Stack, Swap, Toast & Tooltip -->
            <div class="md:col-span-2 space-y-4 border p-4 rounded-box">
              <h3 class="text-xl font-bold">Stack, Swap, Toast & Tooltip</h3>
              <div class="flex flex-wrap items-end justify-center space-x-8 space-y-4">
                <div class="stack stack-xs">
                  <div class="card shadow-md bg-primary text-primary-content w-20">
                    <div class="card-body items-center text-center p-2">A</div>
                  </div>
                  <div class="card shadow-md bg-secondary text-secondary-content w-20 translate-x-3 translate-y-3">
                    <div class="card-body items-center text-center p-2">B</div>
                  </div>
                  <div class="card shadow-md bg-accent text-accent-content w-20 translate-x-6 translate-y-6">
                    <div class="card-body items-center text-center p-2">C</div>
                  </div>
                </div>

                <label class="swap swap-flip text-4xl">
                  <input type="checkbox" />
                  <div class="swap-on">🤯</div>
                  <div class="swap-off">😀</div>
                </label>
                
                <div class="tooltip tooltip-right" data-tip="Hello, I am a tooltip!">
                  <button class="btn btn-ghost">Hover me</button>
                </div>
              </div>

              <div class="toast toast-end mt-4">
                <div class="alert alert-info">
                  <span>Toast notification placeholder.</span>
                </div>
              </div>
            </div>

            <!-- Calendar -->
            <div class="space-y-4 border p-4 rounded-box">
              <h3 class="text-xl font-bold">Calendar</h3>
              <input type="date" class="input input-bordered w-full" />
            </div>

          </div>
        </div>

      </div>
    </div>
  </AppLayout>
</template>