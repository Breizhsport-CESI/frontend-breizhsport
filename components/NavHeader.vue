<template>
    <div class="bg-white">
      <!-- Mobile menu -->
      <TransitionRoot as="template" :show="open">
        <Dialog as="div" class="fixed inset-0 flex z-40 lg:hidden" @close="open = false">
          <TransitionChild as="template" enter="transition-opacity ease-linear duration-300" enter-from="opacity-0" enter-to="opacity-100" leave="transition-opacity ease-linear duration-300" leave-from="opacity-100" leave-to="opacity-0">
            <DialogOverlay class="fixed inset-0 bg-black bg-opacity-25" />
          </TransitionChild>
  
          <TransitionChild as="template" enter="transition ease-in-out duration-300 transform" enter-from="-translate-x-full" enter-to="translate-x-0" leave="transition ease-in-out duration-300 transform" leave-from="translate-x-0" leave-to="-translate-x-full">
            <div class="relative max-w-xs w-full bg-white shadow-xl pb-12 flex flex-col overflow-y-auto">
              <div class="px-4 pt-5 pb-2 flex">
                <button type="button" class="-m-2 p-2 rounded-md inline-flex items-center justify-center text-gray-400" @click="open = false">
                  <span class="sr-only">Close menu</span>
                  <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                </button>
              </div>
  
              <div class="border-t border-gray-200 py-6 px-4 space-y-6">
                <div v-for="page in navigation.pages" :key="page.name" class="flow-root">
                  <a :href="page.href" class="-m-2 p-2 block font-medium text-gray-900">{{ page.name }}</a>
                </div>
              </div>
  
              <div class="border-t border-gray-200 py-6 px-4 space-y-6">
                <div class="flow-root">
                  <a href="#" class="-m-2 p-2 block font-medium text-gray-900">Se connecter</a>
                </div>
                <div class="flow-root">
                  <a href="#" class="-m-2 p-2 block font-medium text-gray-900">S'enregistrer</a>
                </div>
              </div>
  
              <!-- <div class="border-t border-gray-200 py-6 px-4">
                <a href="#" class="-m-2 p-2 flex items-center">
                  <img src="https://tailwindui.com/img/flags/flag-canada.svg" alt="" class="w-5 h-auto block flex-shrink-0" />
                  <span class="ml-3 block text-base font-medium text-gray-900"> CAD </span>
                  <span class="sr-only">, change currency</span>
                </a>
              </div> -->
            </div>
          </TransitionChild>
        </Dialog>
      </TransitionRoot>
  
      <header class="relative bg-white">
        <p class="bg-primary-600 h-10 flex items-center justify-center text-sm font-medium text-white px-4 sm:px-6 lg:px-8">Livraison gratuite à partir de 100 € d'achat</p>
  
        <nav aria-label="Top" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="border-b border-gray-200">
            <div class="h-16 flex items-center">
              <button type="button" class="bg-white p-2 rounded-md text-gray-400 lg:hidden" @click="open = true">
                <span class="sr-only">Open menu</span>
                <Bars3Icon class="h-6 w-6" aria-hidden="true" />
              </button>
  
              <!-- Logo -->
              <div class="ml-4 flex lg:ml-0">
                <a href="#">
                  <span class="sr-only">Workflow</span>
                  <img class="h-8 w-auto" src="https://tailwindui.com/img/logos/workflow-mark.svg?color=indigo&shade=600" alt="" />
                </a>
              </div>
  
              <!-- Flyout menus -->
              <PopoverGroup class="hidden lg:ml-8 lg:block lg:self-stretch">
                <div class="h-full flex space-x-8">
  
                  <a v-for="page in navigation.pages" :key="page.name" :href="page.href" class="flex items-center text-sm font-medium text-gray-700 hover:text-gray-800">{{ page.name }}</a>
                </div>
              </PopoverGroup>
  
              <div class="ml-auto flex items-center">
                <div class="hidden lg:flex lg:flex-1 lg:items-center lg:justify-end lg:space-x-6">
                  <a href="#" class="text-sm font-medium text-gray-700 hover:text-gray-800">Se connecter</a>
                  <span class="h-6 w-px bg-gray-200" aria-hidden="true" />
                  <a href="#" class="text-sm font-medium text-gray-700 hover:text-gray-800">S'enregistrer</a>
                </div>
  
                <!-- <div class="hidden lg:ml-8 lg:flex">
                  <a href="#" class="text-gray-700 hover:text-gray-800 flex items-center">
                    <img src="https://tailwindui.com/img/flags/flag-canada.svg" alt="" class="w-5 h-auto block flex-shrink-0" />
                    <span class="ml-3 block text-sm font-medium"> CAD </span>
                    <span class="sr-only">, change currency</span>
                  </a>
                </div> -->
  
                <!-- Search -->
                <div class="flex lg:ml-6">
                  <a href="#" class="p-2 text-gray-400 hover:text-gray-500">
                    <span class="sr-only">Search</span>
                    <MagnifyingGlassIcon class="w-6 h-6" aria-hidden="true" />
                  </a>
                </div>
  
                <!-- Cart -->
                <div class="ml-4 flow-root lg:ml-6">
                  <a href="#" class="group -m-2 p-2 flex items-center">
                    <ShoppingBagIcon class="flex-shrink-0 h-6 w-6 text-gray-400 group-hover:text-gray-500" aria-hidden="true" />
                    <span class="ml-2 text-sm font-medium text-gray-700 group-hover:text-gray-800">0</span>
                    <span class="sr-only">items in cart, view bag</span>
                  </a>
                </div>
              </div>
            </div>
          </div>
        </nav>
      </header>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue'
  import {
    Dialog,
    DialogOverlay,
    Popover,
    PopoverButton,
    PopoverGroup,
    PopoverPanel,
    Tab,
    TabGroup,
    TabList,
    TabPanel,
    TabPanels,
    TransitionChild,
    TransitionRoot,
  } from '@headlessui/vue'
  import { Bars3Icon, MagnifyingGlassIcon, ShoppingBagIcon, XMarkIcon } from '@heroicons/vue/24/solid'
  
  const navigation = {
    // categories: [
    //   {
    //     id: 'women',
    //     name: 'Femme',
    //     featured: [
    //       {
    //         name: 'New Arrivals',
    //         href: '#',
    //         imageSrc: 'https://tailwindui.com/img/ecommerce-images/mega-menu-category-01.jpg',
    //         imageAlt: 'Models sitting back to back, wearing Basic Tee in black and bone.',
    //       },
    //       {
    //         name: 'Basic Tees',
    //         href: '#',
    //         imageSrc: 'https://tailwindui.com/img/ecommerce-images/mega-menu-category-02.jpg',
    //         imageAlt: 'Close up of Basic Tee fall bundle with off-white, ochre, olive, and black tees.',
    //       },
    //     ],
    //     sections: [
    //       {
    //         id: 'clothing',
    //         name: 'Clothing',
    //         items: [
    //           { name: 'Tops', href: '#' },
    //           { name: 'Dresses', href: '#' },
    //           { name: 'Pants', href: '#' },
    //           { name: 'Denim', href: '#' },
    //           { name: 'Sweaters', href: '#' },
    //           { name: 'T-Shirts', href: '#' },
    //           { name: 'Jackets', href: '#' },
    //           { name: 'Activewear', href: '#' },
    //           { name: 'Browse All', href: '#' },
    //         ],
    //       },
    //       {
    //         id: 'accessories',
    //         name: 'Accessories',
    //         items: [
    //           { name: 'Watches', href: '#' },
    //           { name: 'Wallets', href: '#' },
    //           { name: 'Bags', href: '#' },
    //           { name: 'Sunglasses', href: '#' },
    //           { name: 'Hats', href: '#' },
    //           { name: 'Belts', href: '#' },
    //         ],
    //       },
    //       {
    //         id: 'brands',
    //         name: 'Brands',
    //         items: [
    //           { name: 'Full Nelson', href: '#' },
    //           { name: 'My Way', href: '#' },
    //           { name: 'Re-Arranged', href: '#' },
    //           { name: 'Counterfeit', href: '#' },
    //           { name: 'Significant Other', href: '#' },
    //         ],
    //       },
    //     ],
    //   },
    //   {
    //     id: 'men',
    //     name: 'Homme',
    //     featured: [
    //       {
    //         name: 'New Arrivals',
    //         href: '#',
    //         imageSrc: 'https://tailwindui.com/img/ecommerce-images/product-page-04-detail-product-shot-01.jpg',
    //         imageAlt: 'Drawstring top with elastic loop closure and textured interior padding.',
    //       },
    //       {
    //         name: 'Artwork Tees',
    //         href: '#',
    //         imageSrc: 'https://tailwindui.com/img/ecommerce-images/category-page-02-image-card-06.jpg',
    //         imageAlt:
    //           'Three shirts in gray, white, and blue arranged on table with same line drawing of hands and shapes overlapping on front of shirt.',
    //       },
    //     ],
    //     sections: [
    //       {
    //         id: 'clothing',
    //         name: 'Clothing',
    //         items: [
    //           { name: 'Tops', href: '#' },
    //           { name: 'Pants', href: '#' },
    //           { name: 'Sweaters', href: '#' },
    //           { name: 'T-Shirts', href: '#' },
    //           { name: 'Jackets', href: '#' },
    //           { name: 'Activewear', href: '#' },
    //           { name: 'Browse All', href: '#' },
    //         ],
    //       },
    //       {
    //         id: 'accessories',
    //         name: 'Accessories',
    //         items: [
    //           { name: 'Watches', href: '#' },
    //           { name: 'Wallets', href: '#' },
    //           { name: 'Bags', href: '#' },
    //           { name: 'Sunglasses', href: '#' },
    //           { name: 'Hats', href: '#' },
    //           { name: 'Belts', href: '#' },
    //         ],
    //       },
    //       {
    //         id: 'brands',
    //         name: 'Brands',
    //         items: [
    //           { name: 'Re-Arranged', href: '#' },
    //           { name: 'Counterfeit', href: '#' },
    //           { name: 'Full Nelson', href: '#' },
    //           { name: 'My Way', href: '#' },
    //         ],
    //       },
    //     ],
    //   },
    // ],
    pages: [
      { name: 'Femme', href: '/' },
      { name: 'Homme', href: '/' },
      { name: 'Equipement', href: '#' },
      // { name: 'Company', href: '#' },
      // { name: 'Stores', href: '#' },
    ],
  }
  
  export default {
    components: {
      Dialog,
      DialogOverlay,
      Popover,
      PopoverButton,
      PopoverGroup,
      PopoverPanel,
      Tab,
      TabGroup,
      TabList,
      TabPanel,
      TabPanels,
      TransitionChild,
      TransitionRoot,
      Bars3Icon,
      MagnifyingGlassIcon,
      ShoppingBagIcon,
      XMarkIcon,
    },
    setup() {
      const open = ref(false)
  
      return {
        navigation,
        open,
      }
    },
  }
  </script>