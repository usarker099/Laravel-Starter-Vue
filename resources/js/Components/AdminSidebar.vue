<script setup>
import { Link, usePage } from '@inertiajs/vue3'
import { defineProps } from 'vue';

const props = defineProps({
    items: {
        type: Array,
        required: true,
        default: () => []
    },
});

const page = usePage();

const isActive = (href) => {
    return page.url.startsWith(href) && href !== '/';
};
</script>

<template>
  <ul class="menu bg-base-200 w-56 xs:w-64 min-h-full p-2 xs:p-4 text-xs xs:text-base text-base-content">
    <h2 class="text-lg xs:text-xl font-bold mb-2 xs:mb-4">Menu</h2>

    <li v-for="(item, index) in items" :key="index">
      <template v-if="item.children && item.children.length">
        <details :open="item.children.some(child => isActive(child.href))">
          <summary class="text-xs xs:text-sm">
            <Link 
              :href="item.href || '#'" 
              :class="{ 'active': isActive(item.href) }"
              class="flex items-center"
            >
              <span>{{ item.label }}</span>
            </Link>
          </summary>
          <ul class="p-2 bg-base-100 rounded-box ml-4">
            <li v-for="(child, cIndex) in item.children" :key="cIndex">
              <template v-if="child.children && child.children.length">
                <details :open="child.children.some(subchild => isActive(subchild.href))">
                  <summary class="text-xs xs:text-sm">
                    <Link 
                      :href="child.href || '#'" 
                      :class="{ 'active': isActive(child.href) }"
                      class="flex items-center"
                    >
                      <span>{{ child.label }}</span>
                    </Link>
                  </summary>
                  <ul class="p-2 bg-base-200 rounded-box ml-4">
                    <li v-for="(subchild, scIndex) in child.children" :key="scIndex">
                      <Link 
                        :href="subchild.href" 
                        :class="{ 'active': isActive(subchild.href) }"
                        class="text-xs xs:text-sm block py-1"
                      >
                        {{ subchild.label }}
                      </Link>
                    </li>
                  </ul>
                </details>
              </template>
              <template v-else>
                <Link 
                  :href="child.href" 
                  :class="{ 'active': isActive(child.href) }"
                  class="text-xs xs:text-sm block py-1"
                >
                  {{ child.label }}
                </Link>
              </template>
            </li>
          </ul>
        </details>
      </template>
      <template v-else>
        <Link 
          :href="item.href" 
          :class="{ 'active': isActive(item.href) }"
          class="text-xs xs:text-sm block py-1"
        >
          {{ item.label }}
        </Link>
      </template>
    </li>
    <li>
    <Link href="/dashboard2" class="text-xs xs:text-sm block py-1">Dashboard2</Link>
    </li>

    <li class="mt-4 pt-2 border-t border-base-300">
      <details :open="false">
        <summary class="text-xs xs:text-sm cursor-pointer">
          <span class="flex items-center">Settings</span>
        </summary>
        <ul class="p-2 bg-base-100 rounded-box ml-4">

          <li>
            <details :open="false">
              <summary class="text-xs xs:text-sm cursor-pointer">
                <span class="flex items-center">User</span>
              </summary>
              <ul class="p-2 bg-base-200 rounded-box ml-4">
                <li>
                  <Link href="users" class="text-xs xs:text-sm block py-1">Manage User </Link>
                </li>

              </ul>
            </details>
          </li>
          <li>
            <details :open="false">
              <summary class="text-xs xs:text-sm cursor-pointer">
                <span class="flex items-center">Role & Permission</span>
              </summary>
              <ul class="p-2 bg-base-200 rounded-box ml-4">
                <li>
                  <Link href="roles" class="text-xs xs:text-sm block py-1">Manage Role</Link>
                </li>
                <li>
                  <Link href="permissions" class="text-xs xs:text-sm block py-1">Manage Permission</Link>
                </li>

              </ul>
            </details>
          </li>
          <li>
            <Link href="/home" class="text-xs xs:text-sm block py-1">Home</Link>
          </li>
        </ul>
      </details>
    </li>
    
  </ul>
</template>