<template>
  <div class="relative mx-auto">
    <img
      width="1400"
      height="800"
      class="object-cover rounded-lg w-full h-[420px] lg:h-[560px] xl:h-[640px]"
      src="../../public//images/banner1.jpg"
      alt="Hero image"
      loading="eager"
      format="webp"
      fit="outside"
      sizes="sm:100vw lg:1400px"
      fetchpriority="high"
      preload />
    <div class="container absolute inset-0 flex flex-col items-start justify-center text-gray-100 bg-gradient-to-l from-gray-800 md:bg-none p-8">
      <h1 class="text-3xl font-bold md:mb-4 md:text-4xl lg:text-6xl">Just landed.</h1>
      <h2 class="text-lg font-bold md:mb-4 lg:text-3xl">Latest Collections</h2>
      <div class="max-w-sm mb-8 text-md font-light lg:max-w-md">
        <p>Our Latest Collections are here! We have a wide range of products to make you feel extra special.</p>
      </div>
      <NuxtLink class="px-6 py-3 font-bold text-black bg-[#E9A7AF] rounded-xl hover:bg-[#f1c5ca]" to="/products">Shop now </NuxtLink>
    </div>
  </div>
</template>
