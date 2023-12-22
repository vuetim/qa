<script setup lang="ts">
interface ProductPriceProps {
  regularPrice?: string | null;
  salePrice?: string | null;
}

const { regularPrice, salePrice } = defineProps<ProductPriceProps>();

const formatPrice = (price: string | null) => {
  return price ? price.replace(/&nbsp;/g, '') : '';
};
</script>

<template>
  <div v-if="regularPrice" class="flex">
    <span class="font-semibold" :class="{ 'text-gray-400 line-through font-normal': salePrice }" v-html="formatPrice(regularPrice)" />
    <span v-if="salePrice" class="font-semibold ml-2">{{ formatPrice(salePrice) }}</span>
  </div>
</template>
