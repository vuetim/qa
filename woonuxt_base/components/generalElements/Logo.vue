<script setup lang="ts">
const runtimeConfig = useRuntimeConfig();
const logoUrl = runtimeConfig?.public?.LOGO || null;
const isProduction = process.env.NODE_ENV === 'production';
</script>

<template>
  <NuxtLink to="/">
    <img v-if="logoUrl" :src="logoUrl" alt="Logo" class="object-contain h-10" />
    <div v-else class="flex items-center gap-4 w-[280] text-lg font-bold">
      <NuxtImg :src="isProduction ? '/_vercel/image?url=/images/logoqaf.png' : '/images/logoqaf.png'" width="400" height="80" />
    </div>
  </NuxtLink>
</template>
