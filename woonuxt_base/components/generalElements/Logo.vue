<script setup lang="ts">
const runtimeConfig = useRuntimeConfig();
const logoUrl = runtimeConfig?.public?.LOGO || null;
</script>

<template>
  <NuxtLink to="/">
    <img v-if="logoUrl" :src="logoUrl" alt="Logo" class="object-contain h-10" />
    <div v-else class="flex items-center gap-4 sm:w-[120]  w-32 h-8 text-lg font-bold">
      <img src="../../public/logoqaf.png" />
    </div>
  </NuxtLink>
</template>
