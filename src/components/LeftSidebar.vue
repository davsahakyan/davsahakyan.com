<script setup>
import { ref } from 'vue';


const list = ref([
  {
    "section": "about",
    "text": "About"
  },
  {
    "section": "experience",
    "text": "Experience"
  },
  {
    "section": "projects",
    "text": "Projects"
  }
]);

const listRefs = ref([]);

</script>

<template>
  <div>
    <div id="heading">
      <div id="name">David Sahakyan</div>
      <div id="position">Web Developer</div>
    </div>

    <nav id="menu">
      <ul id="menu_list">
        <li v-for="litem in list" :key="litem.section" :class="litem.section" ref="listRefs">
          {{ litem.text }}
        </li>
      </ul>
    </nav>

  </div>
  <div id="socials">
    <div class="social"></div>
    <div class="social"></div>
    <div class="social"></div>
    <div class="social"></div>
  </div>
</template>

<style scoped>
#heading #name {
  font-size: 48px;
  font-weight: 600;
  line-height: 0.7;
  margin-top: .3em;
}

#heading #position {
  font-size: 36px;
  font-weight: 200;
}

ul#menu_list {
  list-style-type: none;
}

ul#menu_list {
  padding: 0;
  padding-top: 6em;
}

ul#menu_list li {
  font-size: 28px;
  color: var(--d-white-o-40);
  transition: .5s ease;
  transform-origin: left bottom;
  height: 60px;
  line-height: 60px;
  user-select: none;
  -webkit-user-drag: none;
}

ul#menu_list li.active {
  font-size: 40px;
  color: var(--d-white);
}
</style>
