<script setup>
import ExperienceSingle from './ExperienceSingle.vue';


</script>

<template>
    <section id="experience">
        <ExperienceSingle :skills-used="['Nuxt.js', 'Vue.js', 'JavaScript', 'CSS', 'WordPress']">
            <template v-slot:date>
                March 2024 — Present
            </template>
            <template v-slot:position>
                <span>Front-End Developer</span> • SayNine
            </template>
            <template v-slot:description>
                I am responsible for developing and maintaining front-end of tools for in-house usage, as well as
                developing and maintaining our website.
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
                With the team, we have built a program for displaying advertisements on major local websites using
                Javascript.
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
                Built 800+ animated advertisement banners, developed CMS-powered websites , and crafted internally used
                tools to maximize working efficiency.
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
}

section#experience:hover .experience-wrapper:hover {
    opacity: 1;
}
</style>