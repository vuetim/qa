<script setup lang="ts">
const { toggleMobileMenu } = useHelpers();
</script>

<template>
  <div>
    <Icon name="ion:menu-outline" color="black" size="26" class="mr-4 cursor-pointer" @click="toggleMobileMenu" />
  </div>
</template>
