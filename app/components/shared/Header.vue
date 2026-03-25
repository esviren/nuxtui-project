<script setup lang="ts">
import type { NavigationMenuItem, DropdownMenuItem } from '@nuxt/ui';

const route = useRoute();


const languageItems = ref<DropdownMenuItem[]>([
  {
    label: 'Profile',
    icon: 'i-lucide-user'
  },
  {
    label: 'Billing',
    icon: 'i-lucide-credit-card'
  },
  {
    label: 'Settings',
    icon: 'i-lucide-cog'
  }
]);

const items = computed<NavigationMenuItem[]>(() => [{
  label: 'Productos',
  to: '/products',
  //icon: 'i-lucide-book-open',
  active: route.path.startsWith('/products')
}, {
  label: 'Precios',
  to: '/pricing',
  //icon: 'i-lucide-box',
  active: route.path.startsWith('/pricing')
}, {
  label: 'Nosotros',
  //icon: 'i-simple-icons-figma',
  to: '/about',
  active: route.path.startsWith('/about')
}, {
  label: 'Contacto',
  //icon: 'i-lucide-rocket',
  to: '/contact',
  target: '_blank'
}]);
</script>

<template>
  <UHeader
    :toggle="{
      color: 'primary',
      variant: 'subtle',
      class: 'rounded-full'
    }"
  >
    <template #title>
      <IconsNuxtUI class="h-6 w-auto" />
    </template>

    <UNavigationMenu :items="items" />

    <template #right>
      <UColorModeButton />

      <UTooltip text="Open on GitHub" :kbds="['meta', 'G']">
        <UButton
          color="neutral"
          variant="ghost"
          to="https://github.com/nuxt/ui"
          target="_blank"
          icon="i-simple-icons-github"
          aria-label="GitHub"
        />
      </UTooltip>
      <UDropdownMenu
        :items="languageItems"
        :content="{
          align: 'start',
          side: 'bottom',
          sideOffset: 8
        }"
        :ui="{
          content: 'w-48'
        }"
      >
        <UButton label="Open" icon="i-lucide-menu" color="neutral" variant="outline" />
      </UDropdownMenu>
    </template>

    <template #body>
      <UNavigationMenu :items="items" orientation="vertical" class="-mx-2.5" />
    </template>
  </UHeader>
</template>

