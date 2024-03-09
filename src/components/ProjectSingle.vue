<script setup>
defineProps({
    imageUrl: String,
    imageAlt: String,
    buttonColor: String
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
            <button class="action-button" :style="'--action-button-color: ' + buttonColor">
                <slot name="actionText">

                </slot>
            </button>

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

.project-wrapper .image {
    width: 40%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    overflow: hidden;
}

.project-wrapper .description {
    font-size: 16px;
    line-height: 1.2em;
    padding-right: 2em;
}

.project-wrapper .image img {
    aspect-ratio: 16 / 9;
    height: 100%;
}

.action-button {
    background-color: #090732;
    border: none;
    outline: none;
    color: #fff;
    font-weight: 900;
    padding: .3em 1.8em;
    border-radius: 2px;
    font-size: 16px;
    width: max-content;
    background-color: var(--action-button-color);
}
</style>