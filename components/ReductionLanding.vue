<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <div class="bg-white relative overflow-hidden">
    <!-- Decorative background image and gradient -->
    <div aria-hidden="true" class="absolute inset-0">
      <div class="absolute inset-0 max-w-7xl mx-auto overflow-hidden xl:px-8">
        <img src="../assets/ReducLanding.webp" alt="" class="w-full h-full object-center object-cover" />
      </div>
      <div class="absolute inset-0 bg-white bg-opacity-25" />
      <!-- <div class="absolute inset-0 bg-gradient-to-t from-white via-white" /> -->
      <div class="absolute bottom-0 h-1/2 w-full bg-gradient-to-t from-white via-white" />

    </div>

    <!-- Callout -->
    <section aria-labelledby="sale-heading"
      class="relative max-w-7xl mx-auto pt-32 px-4 flex flex-col items-center text-center sm:px-6 lg:px-8">
      <div class="max-w-2xl mx-auto lg:max-w-none">
        <h2 id="sale-heading" class="text-4xl font-extrabold tracking-tight text-gray-900 sm:text-5xl lg:text-6xl">
          Profitez de -25 %</h2>
        <p class="mt-4 max-w-xl mx-auto text-xl text-gray-800">La plupart de nos produits sont des éditions limitées qui
          ne reviendront pas. Obtenez vos articles préférés tant qu'ils sont encore en stock.</p>
        <a href="#"
          class="mt-6 inline-block w-full bg-gray-900 border border-transparent rounded-md py-3 px-8 font-medium text-white hover:bg-gray-800 sm:w-auto">Accédez
          à notre vente unique</a>
      </div>
    </section>


  </div>
</template>