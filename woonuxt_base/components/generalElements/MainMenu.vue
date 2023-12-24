<template>
  <nav>
    <NuxtLink class="text-black font-semibold hover:text-[#b17c82] hover:border-b-2 border-b-[#E9A7AF] duration-300"
      to="/">{{
        $t('messages.general.home') }}</NuxtLink>
    <NuxtLink class="text-black font-semibold hover:text-[#b17c82] hover:border-b-2 border-b-[#E9A7AF] duration-300"
      to="/products">{{
        $t('messages.general.allProducts') }}</NuxtLink>
    <NuxtLink class="text-black font-semibold hover:text-[#b17c82] hover:border-b-2 border-b-[#E9A7AF] duration-300"
      to="/categories">{{
        $t('messages.shop.category', 2) }}</NuxtLink>
    <NuxtLink class="text-black font-semibold hover:text-[#b17c82] hover:border-b-2 border-b-[#E9A7AF] duration-300"
      to="/contact">{{
        $t('messages.general.contact') }}</NuxtLink>

    <NuxtLink class="lg:hidden" to="/wishlist" :prefetch="false">Wishlist</NuxtLink>
    <NuxtLink class="lg:hidden" to="/my-account" :prefetch="false">My Account</NuxtLink>
  </nav></template>
