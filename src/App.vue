<script setup lang="ts">
  import NavView from './views/NavView.vue'
</script>

<template>
  <NavView />
  <main>
    <RouterView />
  </main>
</template>

<style>
  main {
    padding: 1rem 2rem;
    width: calc(100vw - 4rem);
  }
</style>