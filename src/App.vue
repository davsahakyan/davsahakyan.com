<script setup>
import LeftSidebar from './components/LeftSidebar.vue';

</script>

<template>
  <header id="container">
    <div id="sidebar">
      <LeftSidebar />
    </div>
  </header>
</template>

<style scoped>
  #sidebar {
    width: max-content;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

</style>
