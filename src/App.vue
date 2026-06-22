<script setup>
import { RouterView } from 'vue-router'
import headerCompo from './components/headerCompo.vue';
import footerCompo from './components/footerCompo.vue';
</script>

<template>
  <headerCompo />
  <RouterView />
  <footerCompo />
</template>

<style scoped>
</style>
