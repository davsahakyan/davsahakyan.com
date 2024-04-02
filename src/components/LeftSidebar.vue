<script setup>
import { onMounted, ref } from 'vue';

import GithubIcon from '../assets/Github.svg';
import LinkedInIcon from '../assets/LinkedIn.svg';
import FiverrIcon from '../assets/Fiverr.svg';
import UpworkIcon from '../assets/Upwork.svg';

const list = ref([
  {
    "section": "about",
    "text": "About",
    active: true
  },
  {
    "section": "experience",
    "text": "Experience",
    active: false
  },
  {
    "section": "projects",
    "text": "Projects",
    active: false
  }
]);

const socials = ref([
  {
    "image": GithubIcon,
    "alt": "Github",
    "url": "https://github.com/davsahakyan"
  },
  {
    "image": LinkedInIcon,
    "alt": "LinkedIn",
    "url": "https://www.linkedin.com/in/dav-sahakyan/"
  },
  {
    "image": FiverrIcon,
    "alt": "Fiverr",
    "url": "https://www.fiverr.com/davsahakyann",
  },
  {
    "image": UpworkIcon,
    "alt": "Upwork",
    "url": "https://www.upwork.com/freelancers/~01df82f3d99133d553",
  }
])

const listRefs = ref([]);

function showSection(sectionId) {
  document.querySelector(`#${sectionId}`)?.scrollIntoView({ behavior: 'smooth' });
}

let headerMenu = null;

function showHeaderOnScroll() {
  if (!headerMenu) return;

  if (window.scrollY > 200) {
    headerMenu.classList.add('showMenu');
  } else {
    headerMenu.classList.remove('showMenu');
  }
}

window.addEventListener('scroll', showHeaderOnScroll);
window.addEventListener('resize', showHeaderOnScroll);

onMounted(() => {
  headerMenu = document.querySelector('nav#menu');

  window.addEventListener('updateActiveNavEvent', (e) => {
    list.value.forEach((li) => {
      li.active = (e.detail.activeSectionId == li.section);
    })
  })
})
</script>

<template>
  <div>
    <div id="heading">
      <div id="name">David Sahakyan</div>
      <div id="position">Web Developer</div>
    </div>

    <nav id="menu">
      <ul id="menu_list">
        <li v-for="litem in list" :key="litem.section" :class="[litem.section, (litem.active) ? 'active' : '']"
          @click="showSection(litem.section)" ref="listRefs">
          <a>
            {{ litem.text }}
          </a>
        </li>
      </ul>
    </nav>
  </div>

  <div id="socials">
    <div class="social" v-for="(social, index) in socials" :key="index">
      <a :href="social.url" target="_blank">
        <img :src="social.image" :alt="social.alt">
      </a>
    </div>
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
  font-size: 24px;
  color: var(--d-white-o-40);
  transform-origin: left bottom;
  height: 60px;
  line-height: 60px;
  user-select: none;
  -webkit-user-drag: none;
}

ul#menu_list li a {
  color: inherit;
  cursor: pointer;
  text-decoration: none;
  transition: .3s ease;
}

ul#menu_list li a:hover {
  color: var(--d-white-o-80);
}

ul#menu_list li.active a {
  font-size: 36px;
  color: var(--d-white);
  transition: .4 s ease;
}

#socials {
  margin-top: 10vh;
  width: max-content;

}

#socials:hover .social {
  opacity: .4;
}

#socials .social {
  height: 28px;
  display: inline-block;
  margin-right: .6em;
  opacity: .9;
  transition: .2s linear;
}

#socials .social:hover,
#socials .social::selection {
  opacity: 1;
}

.social a {
  width: 100%;
  height: 100%;
}

.social a img {
  width: 100%;
  height: 100%;
}

@media screen and (max-width: 1200px) {
  #socials {
    margin-top: 1em;
  }

  #menu {
    width: 100%;
    height: 80px;
    top: -80px;
    opacity: 0;
    left: 0;

    position: fixed;
    transition: .4s ease;

  }

  #menu.showMenu {
    opacity: 1;
    top: 0;
  }

  ul#menu_list {
    width: 100%;
    height: 100%;
    padding-top: 0;
    padding-left: 2em;

    position: relative;
    display: flex;
    align-items: center;

    background: rgb(12, 31, 73);
    background: -moz-linear-gradient(180deg, rgba(12, 31, 73, 0.8) 50%, rgba(0, 0, 0, 0) 100%);
    background: -webkit-linear-gradient(180deg, rgba(12, 31, 73, 0.8) 50%, rgba(0, 0, 0, 0) 100%);
    background: linear-gradient(180deg, rgba(12, 31, 73, 0.8) 50%, rgba(0, 0, 0, 0) 100%);
    filter: progid:DXImageTransform.Microsoft.gradient(startColorstr="#0c1f49", endColorstr="#000000", GradientType=1);
  }

  ul#menu_list li {
    position: absolute;
  }

  ul#menu_list li {
    opacity: 0;
  }

  ul#menu_list li a {
    color: inherit;
    cursor: pointer;
    text-decoration: none;
    transition: .3s ease;
    opacity: 1;
  }

  ul#menu_list li.active {
    opacity: 1;
  }

  ul#menu_list li.active a {
    font-size: 28px;
    color: var(--d-white);
    transition: .4 s ease;
  }
}
</style>
