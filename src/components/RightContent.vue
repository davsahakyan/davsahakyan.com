<script setup>
import { onMounted } from 'vue';
import AboutSection from './AboutSection.vue';

function getTopDistance(element) {
    const rect = element.getBoundingClientRect();
    return Math.abs(rect.top);
}

function updateActiveSection()  {
    const sections = document.querySelectorAll('section#content section');
    const navLinks = document.querySelectorAll('nav#menu ul li');

    let minTopDistance = window.innerHeight;
    let activeSection = null;

    
    sections.forEach((section) => {
        const topDistance = getTopDistance(section);

        if (topDistance < minTopDistance) {
            minTopDistance = topDistance;
            activeSection = section.getAttribute('id');
        }
    })

    navLinks.forEach(navLink => {
        if (navLink.classList.contains(activeSection)) {
            navLink.classList.add('active');
        } else {
            navLink.classList.remove('active');
        }
    })
}

onMounted(() => {
    window.addEventListener('scroll', updateActiveSection);
    window.addEventListener('resize', updateActiveSection);
})
</script>

<template>
    <section id="content">
        <AboutSection />
        <section id="experience"></section>
        <section id="projects"></section>
    </section>
</template>

<style scoped>
#content {
    width: 55%;
    padding: 6vh 0;
    scroll-padding-top: 6rem;
}

#experience {
    height: 100vh;
}

#projects {
    height: 100vh;
}
</style>