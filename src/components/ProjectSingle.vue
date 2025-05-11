<script setup>
import ProjectPopUp from './ProjectPopUp.vue';

defineProps({
    imageUrl: String,
    imageAlt: String,
    buttonColor: String,
    websiteUrl: String
})

</script>

<template>
    <div class="project-wrapper">
        <div class="content">
            <div class="info">
                <h2 class="name">
                    <slot name="name">

                    </slot>
                </h2>
                <div class="date">
                    <slot name="date">

                    </slot>
                </div>
            </div>
            <div class="description">
                <slot name="description"></slot>
            </div>

            <!-- <button class="action-button" :style="'--action-button-color: ' + buttonColor">
                <a :href="websiteUrl" target="_blank">
                    <slot name="actionText">
                        
                    </slot>
                </a> 
            </button> -->
            <ProjectPopUp :buttonColor="buttonColor" :image-url='imageUrl' :image-alt="imageAlt" :websiteUrl="websiteUrl">
                <template v-slot:buttonText>
                    Visit
                </template>

                <template v-slot:title>
                    <slot name="name"></slot>
                </template>

                <template v-slot:date>
                    <slot name="date"></slot>
                </template>

                <template v-slot:description>
                    <slot name="description"></slot>
                </template>

            </ProjectPopUp>

        </div>
        <div class="image">
            <img :src="imageUrl" :alt="!!imageAlt ? imageAlt : 'Project Image'">
        </div>
    </div>
</template>

<style scoped>
.project-wrapper {
    width: 100%;
    display: flex;
    height: 200px;
    margin-bottom: 1.5em;
}

.project-wrapper .content {
    width: 60%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    background-color: var(--d-white-o-10);
    padding: 1em 0 1em 1em;
}

.project-wrapper .info h2 {
    font-weight: bold;
    line-height: .8em;
}

.project-wrapper .info .date {
    position: relative;
}

.project-wrapper .description {
    font-size: 16px;
    line-height: 1.2em;
    padding-right: 2em;
}

.project-wrapper .image {
    width: 40%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    overflow: hidden;
    background-color: rgb(30 46 83 / 50%);
}

.project-wrapper .image img {
    height: 100%;
}

@media screen and (max-width: 768px) {
    .project-wrapper {
        flex-direction: column;
        height: auto;
    }

    .project-wrapper .content {
        width: 100%;
        padding: 1em;
        row-gap: 12px;
    }

    .project-wrapper .image {
        width: 100%;
    }

    .project-wrapper .image img {
        width: 100%;
        height: auto;
    }
}

</style>