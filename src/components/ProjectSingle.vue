<script setup>
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
            <button class="action-button" :style="'--action-button-color: ' + buttonColor">
                <a :href="websiteUrl" target="_blank">
                    <slot name="actionText">
                        
                    </slot>
                </a>
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
    height: 100%;
}

.action-button {
    border: none;
    outline: none;
    color: #fff;
    border-radius: 2px;
    width: max-content;
    background-color: transparent;
    cursor: pointer;
    box-shadow: 0px 0px 0 2px rgba(var(--action-button-color), .7);
    transition: box-shadow .4s ease .2s, background-color .6s ease;
}

.action-button:hover {
    background-color: rgba(var(--action-button-color), 1);
    box-shadow: 0px 0px 0 1px rgba(var(--action-button-color), .7);
    transition: box-shadow .3s ease, background-color .7s ease;
}

.action-button a {
    display: block;
    width: 100%;
    height: 100%;
    font-size: 16px;
    font-weight: 900;
    color: #fff;
    text-decoration: none;
    padding: .3em 2em;
}
</style>