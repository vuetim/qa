<script setup>
const { formatURI } = useHelpers();
const route = useRoute();
const { addToCart, isUpdatingCart } = useCart();

const props = defineProps({
  node: { type: Object, default: null },
  index: { type: Number, default: 1 },
});
const filterQuery = ref(route.query.filter);

// method to add to cart the product
const isAddingToCart = ref(false);

const addToCartHandler = async () => {
  isAddingToCart.value = true;

  const addToCartInput = {
    productId: props.node.databaseId,
    quantity: 1, // Adjust the quantity as needed
  };

  try {
    await addToCart(addToCartInput);
  } finally {
    isAddingToCart.value = false;
  }
};
const paColor = ref(filterQuery.value?.split('pa_color[')[1]?.split(']')[0]?.split(',') || []);

const imgWidth = 220;
const imgHeight = Math.round(imgWidth * 1.125);

const mainImage = computed(() => props.node?.image?.sourceUrl);
const colorVariableImage = computed(() => {
  if (paColor.value.length) {
    const activeColorImage = props.node?.variations?.nodes.filter((variation) => {
      const hasMatchingAttributes = variation.attributes.nodes.some((attribute) => paColor.value.some((color) => attribute.value.includes(color)));
      const hasMatchingSlug = paColor.value.some((color) => variation.slug.includes(color));
      return hasMatchingAttributes || hasMatchingSlug;
    });
    if (activeColorImage && activeColorImage.length) {
      return activeColorImage[0].image?.sourceUrl;
    }
  }
  return null;
});
</script>

<template>
  <div class="relative product-card">
    <NuxtLink :to="`/product/${formatURI(node.slug)}`" :title="node.name">
      <SaleBadge :node="node" class="absolute top-2 right-2" />
      <img
        v-if="colorVariableImage"
        :src="colorVariableImage"
        :alt="node.image?.altText || node.name"
        :title="node.image?.title || node.name"
        :loading="index <= 3 ? 'eager' : 'lazy'" />
      <NuxtImg
        :width="imgWidth"
        :height="imgHeight"
        :src="mainImage || '/images/placeholder.jpg'"
        :alt="node.image?.altText || node.name"
        :title="node.image?.title || node.name"
        :loading="index <= 3 ? 'eager' : 'lazy'"
        fit="outside"
        format="webp"
        densities="x1 x2" />
    </NuxtLink>
    <div class="p-2">
      <StarRating :rating="node.averageRating" :count="node.reviewCount" />
      <NuxtLink :to="`/product/${formatURI(node.slug)}`" :title="node.name">
        <h2 class="mb-2 font-light leading-tight">{{ node.name }}</h2>
      </NuxtLink>
      <ProductPrice class="text-sm" :sale-price="node.salePrice" :regular-price="node.regularPrice" />
      <button
        @click="addToCartHandler"
        :disabled="isUpdatingCart || isAddingToCart"
        class="add-to-cart-button text-white text-sm mt-2 w-full hover:bg-slate-600 bg-black py-2 px-4 rounded-md cursor-pointer">
        {{ isAddingToCart ? 'Adding...' : 'Add to Cart' }}
      </button>
    </div>
  </div>
</template>

<style lang="postcss">
.product-card img {
  @apply rounded-lg object-top object-cover w-full;
  aspect-ratio: 1/1.125;
}
.product-card:hover {
  h2 {
    @apply text-primary;
  }
}
</style>
