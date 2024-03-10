<script setup>
import ProjectSingle from './ProjectSingle.vue';
import g2l from '../assets/global-to-local.jpg';
import edujustice from '../assets/edujusticeforum.jpg';
import ma_ma from '../assets/ma_ma.jpg';

</script>

<template>
    <section id="projects">
        <ProjectSingle :image-url='g2l' image-alt='Global to Local Website' button-color="255, 46, 64">
            <template v-slot:name>
                Global to Local
            </template>
            <template v-slot:date>
                2023, August
            </template>
            <template v-slot:description>
                Fully redesigned a website for an Sweden-based organization “Global to Local”
            </template>
            <template v-slot:actionText>
                Visit
            </template>
        </ProjectSingle>

        <ProjectSingle :image-url='edujustice' image-alt='Edujusticeforum Website' button-color="7, 39, 155">
            <template v-slot:name>
                Edujusticeforum
            </template>
            <template v-slot:date>
                2023, October
            </template>
            <template v-slot:description>
                Built a website for an educational justice forum held regularly in Yerevan, Armenia
            </template>
            <template v-slot:actionText>
                Visit
            </template>
        </ProjectSingle>

        <ProjectSingle :image-url='ma_ma' image-alt='Ma-Ma Banner Board' button-color="46, 134, 86">
            <template v-slot:name>
                Ma-Ma Banners
            </template>
            <template v-slot:date>
                Ongoing
            </template>
            <template v-slot:description>
                Created 40+ animated advertisement banners for a Danish company
            </template>
            <template v-slot:actionText>
                Visit
            </template>
        </ProjectSingle>
    </section>
</template>

<style scoped>
    section#projects {
        padding-top: 1em;
    }
</style>