<script setup>
import LeftSidebar from './components/LeftSidebar.vue';
import RightContent from './components/RightContent.vue';

</script>

<template>
  <div id="container">
    <header>
      <div id="sidebar">
        <LeftSidebar />
      </div>
    </header>
    <RightContent />
  </div>
</template>

<style scoped>
#sidebar {
  width: max-content;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 6vh 0;
  position: sticky;
  top: 0;
}
</style>
