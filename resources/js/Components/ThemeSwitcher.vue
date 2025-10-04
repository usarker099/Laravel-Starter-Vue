<template>
  <div class="dropdown dropdown-end">
    <button type="button" tabindex="0" class="btn m-1">
      Theme: <span class="ml-2 capitalize">{{ theme }}</span>
    </button>

    <ul
      tabindex="0"
      class="dropdown-content z-[1] menu p-2 shadow bg-base-100 rounded-box w-52 max-h-96 overflow-y-auto"
    >
      <li v-for="t in themes" :key="t">
        <button
          type="button"
          class="flex items-center justify-between w-full px-2 py-1 rounded hover:bg-base-200"
          @click="setTheme(t)"
        >
          <span class="capitalize">{{ t }}</span>
          <!-- Live Preview Circle -->
          <span :class="['preview-circle', `bg-preview-${t}`]"></span>
        </button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

// All 35 DaisyUI themes
const themes = [
  'light','dark','cupcake','bumblebee','emerald','corporate','synthwave',
  'retro','cyberpunk','valentine','halloween','garden','forest','aqua',
  'lofi','pastel','fantasy','wireframe','black','luxury','dracula','cmyk',
  'autumn','business','acid','lemonade','night','coffee','winter','forest',
  'bumblebee-light','bumblebee-dark','emerald-light','emerald-dark','retro-light','retro-dark','night-light'
]

// Reactive theme variable
const theme = ref(localStorage.getItem('theme') || 'light')

// Apply the theme
const setTheme = (t) => {
  theme.value = t
  const html = document.querySelector('html')
  if (html) html.setAttribute('data-theme', t)
  localStorage.setItem('theme', t)
}

// On mount, apply the stored theme
onMounted(() => {
  const html = document.querySelector('html')
  if (html) html.setAttribute('data-theme', theme.value)
})
</script>

<style>
/* Circle for live preview */
.preview-circle {
  display: inline-block;
  width: 1rem;
  height: 1rem;
  border-radius: 9999px;
  border: 1px solid #999;
}

/* Live preview colors for each DaisyUI theme (approximation) */
.bg-preview-light { background-color: #f3f4f6; }
.bg-preview-dark { background-color: #1f2937; }
.bg-preview-cupcake { background-color: #fce7f3; }
.bg-preview-bumblebee { background-color: #fefcbf; }
.bg-preview-emerald { background-color: #10b981; }
.bg-preview-corporate { background-color: #ffffff; }
.bg-preview-synthwave { background-color: #ff63c3; }
.bg-preview-retro { background-color: #fef3c7; }
.bg-preview-cyberpunk { background-color: #ff0080; }
.bg-preview-valentine { background-color: #ffe4e6; }
.bg-preview-halloween { background-color: #ff7518; }
.bg-preview-garden { background-color: #dcfce7; }
.bg-preview-forest { background-color: #134e4a; }
.bg-preview-aqua { background-color: #67e8f9; }
.bg-preview-lofi { background-color: #fefce8; }
.bg-preview-pastel { background-color: #fef9c3; }
.bg-preview-fantasy { background-color: #ede9fe; }
.bg-preview-wireframe { background-color: #f5f5f5; }
.bg-preview-black { background-color: #000000; }
.bg-preview-luxury { background-color: #fdf4ff; }
.bg-preview-dracula { background-color: #282a36; }
.bg-preview-cmyk { background-color: #00ffff; }
.bg-preview-autumn { background-color: #ffedd5; }
.bg-preview-business { background-color: #f3f4f6; }
.bg-preview-acid { background-color: #b6ff00; }
.bg-preview-lemonade { background-color: #fff9c0; }
.bg-preview-night { background-color: #0f172a; }
.bg-preview-coffee { background-color: #6b4226; }
.bg-preview-winter { background-color: #e0f2fe; }
/* repeated themes for light/dark variations */
.bg-preview-bumblebee-light { background-color: #fefcbf; }
.bg-preview-bumblebee-dark { background-color: #fcd34d; }
.bg-preview-emerald-light { background-color: #34d399; }
.bg-preview-emerald-dark { background-color: #065f46; }
.bg-preview-retro-light { background-color: #fef3c7; }
.bg-preview-retro-dark { background-color: #fbbf24; }
.bg-preview-night-light { background-color: #1e293b; }
</style>
