<script setup>
import LeftSidebar from './components/LeftSidebar.vue';
import RightContent from './components/RightContent.vue';

const flareContainer = document.querySelector('#flare');

document.body.addEventListener('mousemove', (e) => {
  flareContainer.style.background = `radial-gradient(800px at ${e.clientX}px ${e.clientY}px, var(--flare-color), transparent 70%)`;
})

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
