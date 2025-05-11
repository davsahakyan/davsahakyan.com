<script setup>
defineProps({
    skillsUsed: Array
})
</script>

<template>
    <div class="experience-wrapper">
        <div class="date">
            <slot name="date"></slot>
        </div>
        <div class="content">
            <h3>

                <div class="position">
                    <slot name="position"></slot>
                </div>

                <div class="description">
                    <slot name="description"></slot>
                </div>
                <div class="skills">
                    <span class="skill" v-for="(skill, index) in skillsUsed" :key="index">
                        {{ skill }}
                    </span>
                </div>
            </h3>
        </div>
    </div>
</template>

<style scoped>
.experience-wrapper {
    display: grid;
    grid-template-columns: repeat(8, minmax(0, 1fr));
    gap: 1rem;
    margin-bottom: 1.5em;
    padding: 1em .5em 1em 1em;
    transition: .2s ease;
    border-radius: .2em;
    cursor: default;
}

.experience-wrapper:hover {
    background-color: rgba(255, 255, 255, 0.05);
}

.experience-wrapper .date {
    grid-column: span 2/span 2;
    font-weight: 100;
    font-size: 18px;
}

.experience-wrapper .content {
    grid-column: span 6/span 6;
}

.experience-wrapper .content .position {
    font-size: 26px;
    line-height: 28px;
    padding-bottom: .5em;
}

.experience-wrapper .content .position .span {
    font-weight: 600;
}

.experience-wrapper .content .description {
    font-weight: 200;
    line-height: 30px;
    font-size: 20px;
    padding-bottom: .8em;
    color: var(--d-white-o-80);
}

.experience-wrapper .content .skills {
    --skill-vh-distance: .4em; /* Both vertical and horizontal distance of skill blocks */
    
    display: flex;
    flex-wrap: wrap;
    row-gap: var(--skill-vh-distance);
}

.experience-wrapper .content .skills .skill {
    font-size: 16px;
    padding: .6em 1em .4em 1em;
    margin-right: var(--skill-vh-distance);
    background-color: var(--skill-background);
    color: var(--skill-text);
    line-height: 16px;
    border-radius: 5em;
}

@media screen and (max-width: 768px) {
    .experience-wrapper {
        grid-template-columns: repeat(4, minmax(0, 1fr));
    }

    .experience-wrapper .date {
        grid-column: span 4/span 4;
    }

    .experience-wrapper .content {
        grid-column: span 4/span 4;
    }
}
</style>