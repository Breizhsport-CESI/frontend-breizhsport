<template>
  <Disclosure as="nav" class="bg-secondary fixed inset-x-0 z-50 w-screen shadow backdrop-blur-md">
    <template #default="{ open }">
      <div class="max-w-7xl mx-auto px-2 sm:px-6 lg:px-8">
        <div class="relative flex items-center justify-between h-16">
          <div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
            <!-- Mobile menu button -->
            <DisclosureButton
              class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-white hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white">
              <span class="sr-only">Open main menu</span>
              <Bars3Icon v-if="!open" class="block h-6 w-6" aria-hidden="true" />
              <XMarkIcon v-else class="block h-6 w-6" aria-hidden="true" />
            </DisclosureButton>
          </div>
          <div class="flex-1 flex items-center justify-center sm:items-stretch sm:justify-start">
            <div class="flex-shrink-0 flex items-center">
              <a href="/" class="text-white hover:text-white">
                <!-- <img class="hidden lg:block h-12 w-auto" src="@/assets/logo.webp" alt="NeoProd'Up"/> -->
              </a>
            </div>
            <div class="hidden sm:block sm:ml-6">
              <div class="flex space-x-4">
                <a v-for="item in navigation" :key="item.name" :href="item.href"
                  :class="[item.href == route.currentRoute.value.fullPath ? 'bg-primary text-white' : 'text-black-300 hover:bg-primary hover:text-white', 'px-3 py-2 rounded-md text-sm font-medium']"
                  :aria-current="item.current ? 'page' : undefined">
                  {{ item.name }}
                </a>
              </div>
            </div>
          </div>
          <div v-if="currentRoute.fullPath !== '/login'"
            class="absolute inset-y-0 right-0 flex items-center pr-2 sm:static sm:inset-auto sm:ml-6 sm:pr-0 space-x-4">
            <button @click="toggleColorMode" class="bg-gray-800 text-white p-2 rounded-full hover:bg-gray-700">
              <span class="sr-only">Toggle dark mode</span>
              <SunIcon v-if="colorMode.value === 'dark'" class="h-6 w-6" aria-hidden="true" />
              <MoonIcon v-else class="h-6 w-6" aria-hidden="true" />
            </button>
            <!-- <a href="/login" class="bg-secondary text-secondary px-3 py-2 rounded-md text-sm font-medium border border-primary hover:bg-primary hover:text-white">Log In</a> -->
            <!-- <a v-if="currentRoute.fullPath !== '/login' && !token" href="/login" class="bg-primary text-white px-3 py-2 rounded-md text-sm font-medium hover:bg-primary hover:text-white">Se connecter</a>
                <a v-if="currentRoute.fullPath !== '/login' && token" href="/app" class="bg-primary text-white px-3 py-2 rounded-md text-sm font-medium hover:bg-primary hover:text-white">Accéder à l'application</a> -->
          </div>
        </div>
      </div>

      <DisclosurePanel class="sm:hidden">
        <div class="px-2 pt-2 pb-3 space-y-1">
          <DisclosureButton v-for="item in navigation" :key="item.name" as="a" :href="item.href"
            :class="[item.href == route.currentRoute.value.fullPath ? 'bg-primary text-black' : 'text-black hover:bg-primary hover:text-white dark:text-white', 'block px-3 py-2 rounded-md text-base font-medium']"
            :aria-current="item.current ? 'page' : undefined">
            {{ item.name }}
          </DisclosureButton>
        </div>
      </DisclosurePanel>
    </template>
  </Disclosure>
</template>

<script setup>
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue'
import { Bars3Icon, XMarkIcon, SunIcon, MoonIcon } from '@heroicons/vue/24/solid'
const currentRoute = useRoute()
const route = useRouter()
const props = defineProps({
  navigation: {
    type: Array,
    default: () => [
      { name: 'Accueil', href: '/', current: true },
      { name: 'Mentions légales', href: '/legalnotice', current: false },
      // { name: 'Projects', href: '#', current: false },
      // { name: 'Calendar', href: '#', current: false },
    ]
  },
});
const colorMode = useColorMode()

const toggleColorMode = () => {
  colorMode.preference = colorMode.preference === 'dark' ? 'light' : 'dark'
}
</script>