<script setup>
import { ref } from 'vue';

const heroRevealed = ref(false);
</script>

<template>
  <LoadingOverlay @complete="heroRevealed = true" />
  <NuxtPage :hero-revealed="heroRevealed" />
</template>
