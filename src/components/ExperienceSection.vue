<script setup>
import ExperienceSingle from './ExperienceSingle.vue';


</script>

<template>
    <section id="experience">
        <ExperienceSingle :skills-used="['WordPress', 'Javascript', 'HTML', 'CSS', 'Figma']">
            <template v-slot:date>
                September 2023 - Present
            </template>
            <template v-slot:position>
                <span>Developer</span> • Global to Local
            </template>
            <template v-slot:description>
                Developed and am still maintaining websites representing the organization and projects that it takes on worldwide.
            </template>

        </ExperienceSingle>

        <ExperienceSingle :skills-used="['Javascript', 'Webpack', 'HTML', 'CSS']">
            <template v-slot:date>
                February — November 2023
            </template>
            <template v-slot:position>
                Head of Technical Department • Media Systems
            </template>
            <template v-slot:description>
                With the team, we have built a middleware for displaying advertisements on major local websites using Javascript.
            </template>

        </ExperienceSingle>

        <ExperienceSingle :skills-used="['Javascript', 'HTML', 'CSS', 'CSS3 Animations', 'Google Analytics']">
            <template v-slot:date>
                2021 — February 2023
            </template>
            <template v-slot:position>
                <span>Technical Specialist</span> • Media Systems
            </template>
            <template v-slot:description>
                Built 800+ animated advertisement banners, developed CMS-powered websites , and crafted internally used tools to maximize working efficiency.
            </template>

        </ExperienceSingle>
    </section>
</template>

<style scoped>
    section#experience {
        margin-top: 1em;
        scroll-margin-top: 6vh;
    }

    section#experience:hover .experience-wrapper {
        opacity: 0.5;
        transition: .5s ease;
    }

    section#experience:hover .experience-wrapper:hover {
        opacity: 1;
    }
</style>