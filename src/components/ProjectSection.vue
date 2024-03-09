<script setup>
import ProjectSingle from './ProjectSingle.vue';
import g2l from '../assets/global-to-local.png';

</script>

<template>
    <ProjectSingle :image-url='g2l' image-alt='Global to Local Website' button-color="#ff2e40">
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
</template>

<style scoped></style>