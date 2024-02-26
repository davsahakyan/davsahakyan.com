<script setup>
import { onMounted } from 'vue';
import AboutSection from './AboutSection.vue';
import ExperienceSection from './ExperienceSection.vue';

function getTopDistance(element) {
    const rect = element.getBoundingClientRect();
    return Math.abs(rect.top);
}

let lastActiveSection = null;

function updateActiveSection() {
    const sections = document.querySelectorAll('section#content section');

    let minTopDistance = window.innerHeight;
    let activeSectionId = null;


    sections.forEach((section) => {
        const topDistance = getTopDistance(section);

        if (topDistance < minTopDistance) {
            minTopDistance = topDistance;
            activeSectionId = section.getAttribute('id');
        }
    })

    if (lastActiveSection != activeSectionId) {
        lastActiveSection = activeSectionId;

        let updateActiveNavEvent = new CustomEvent('updateActiveNavEvent', {
            'detail': {
                activeSectionId: activeSectionId,
            }
        })

        window.dispatchEvent(updateActiveNavEvent);
    }

}

onMounted(() => {
    window.addEventListener('scroll', updateActiveSection);
    window.addEventListener('resize', updateActiveSection);
})
</script>

<template>
    <section id="content">
        <AboutSection />
        <ExperienceSection />
        <section id="projects"></section>
    </section>
</template>

<style scoped>
#content {
    width: 55%;
    padding: 6vh 0;
    scroll-padding-top: 6rem;
}

#experience {height: 20px;}

#projects {
    height: 100vh;
}
</style>