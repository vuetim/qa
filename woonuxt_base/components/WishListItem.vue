<script setup lang="ts">
const { removeFromWishlist } = useWishlist();
const { formatURI } = useHelpers();
const { product } = defineProps<{ product: Product }>();
const getAltText = (product: Product): string => {
  return product.image?.altText ?? (product.name || 'Default Alt Text');
};

const getTitleText = (product: Product): string => {
  return product.image?.title ?? (product.name || 'Default Title Text');
};
</script>

<template>
  <li class="flex py-4 gap-4 items-center">
    <button v-if="product.databaseId" title="Remove Item" @click="removeFromWishlist(product.databaseId)">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" width="24" height="24">
        <path fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="32" d="M368 368L144 144M368 144L144 368" />
      </svg>
    </button>
    <NuxtLink :to="`/product/${formatURI(product.slug || '')}`">
      <img
        v-if="product?.image?.cartSourceUrl"
        class="rounded-lg object-cover h-20 w-20"
        :src="product.image?.cartSourceUrl || product.image?.sourceUrl || '/images/placeholder.jpg'"
        :alt="getAltText(product)"
        :title="getTitleText(product)"
        width="100"
        height="120" />
    </NuxtLink>
    <NuxtLink class="text-lg leading-tight" :to="`/product/${formatURI(product.slug || '')}`">{{ product.name }}</NuxtLink>
    <ProductPrice :sale-price="product.salePrice" :regular-price="product.regularPrice" class="ml-auto" />
  </li>
</template>
