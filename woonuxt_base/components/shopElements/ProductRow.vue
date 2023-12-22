<script setup>
const props = defineProps({
  products: { type: Array, default: null },
  showAddToCart: { type: Boolean, default: true }, //  prop to control button visibility
});
</script>

<template>
  <div v-if="products" class="grid gap-8">
    <ProductCard
      v-for="(node, i) in products"
      :key="node.databaseId"
      class="w-full"
      :node="node"
      :index="i"
      :show-add-to-cart="showAddToCart"
      :class="{
        hidden: i === products.length - 1,
        'lg:block': i === products.length - 1,
      }" />
  </div>
</template>
