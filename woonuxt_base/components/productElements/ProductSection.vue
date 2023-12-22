<script setup lang="ts">
const { data, error } = await useAsyncGql('getProducts', { first: 6 });

const products = data.value.products?.nodes as Product[];
</script>

<template>
  <div>
    <section class="container my-16">
      <div class="flex items-end justify-between">
        <h2 class="text-lg font-semibold md:text-2xl">Latest</h2>
        <NuxtLink class="text-primary" to="/products">{{ $t('messages.general.viewAll') }}</NuxtLink>
      </div>
      <div class="grid justify-center grid-cols-2 gap-4 mt-8 md:grid-cols-3 lg:grid-cols-6">
        <ProductList v-for="(product, i) in products" :key="i" class="w-full" :node="product" />
      </div>
    </section>
  </div>
</template>
