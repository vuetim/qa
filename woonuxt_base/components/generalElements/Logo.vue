<script setup lang="ts">
const runtimeConfig = useRuntimeConfig();
const logoUrl = runtimeConfig?.public?.LOGO || null;
</script>

<template>
  <NuxtLink to="/">
    <img v-if="logoUrl" :src="logoUrl" alt="Logo" class="object-contain h-10" />
    <div v-else class="flex items-center gap-4 w-[280] text-lg font-bold">
      <NuxtImg src="/logoqaf.png" width="400" height="80" />
    </div>
  </NuxtLink>
</template>
