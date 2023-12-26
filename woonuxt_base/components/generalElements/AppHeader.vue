<script setup lang="ts">
const { isShowingSearch } = useSearching();
</script>

<template>
  <header class=" top-0 z-40 from-white bg-gradient-to-l shadow-sm shadow-light-500">
    <div class="container flex items-center justify-between py-4">
      <div class="flex items-center">
        <MenuTrigger class="lg:hidden" />
        <Logo class="md:w-[200px]" />
      </div>
      <MainMenu class="items-center uppercase ml-20 hidden gap-6 text-sm text-gray-500 lg:flex lg:px-4" />
      <div class="flex gap-4 justify-end items-center md:w-[160px] flex-1 ml-auto">
        <ProductSearch class="hidden sm:inline-flex max-w-[320px] w-[60%]" />
        <SearchTrigger />
        <NuxtLink to="/wishlist" title="Wishlist">
          <Icon name="ion:heart-outline" size="20" color="black" />
        </NuxtLink>
        <SignInLink />
        <CartTrigger />
      </div>
    </div>
    <Transition name="scale-y" mode="out-in">
      <div class="container mb-3 -mt-1 sm:hidden" v-if="isShowingSearch">
        <ProductSearch class="flex w-full" />
      </div>
    </Transition>
  </header>
</template>
