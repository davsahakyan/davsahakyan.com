<script setup>
import { ref, computed } from 'vue';

defineProps({
    imageUrl: String,
    imageAlt: String,
    websiteUrl: String,
    buttonColor: String
});

const showPopup = ref(false);
const customDiv = ref(null);
const revealPopup = ref(false);

const revealClassObject = computed(() => ({
    popup: revealPopup.value,
}))

const toggle = () => {
    showPopup.value = !showPopup.value;
    setTimeout(() => {
        revealPopup.value = !revealPopup.value
    })
};

const closePopup = () => {
    revealPopup.value = false;
    setTimeout(() => {
        showPopup.value = false;
    }, 200)
};
</script>

<template>
    <div ref="customDiv">
        <button class="action-button" :style="'--action-button-color: ' + buttonColor" @click="toggle">
            <slot name="buttonText" />
        </button>

        <div v-if="showPopup" :class="revealClassObject" @click.stop>

            <div id="popup-wrapper">
                <div class="popup-filter-blur"></div>
                <div class="project-popup">
                    <div class="popup-info">
                        <div class="popup-image">
                    <img :src="imageUrl" :alt="!!imageAlt ? imageAlt : 'Project Image'">
                        </div>
                        <div class="popup-details">
                            <h1>
                                <span class="field-description">Title</span><slot name="title"></slot>
                            </h1>
                            <h4>
                                <span class="field-description">Date</span><slot name="date"></slot>
                            </h4>
                            <div class="popup-visit-button">
                                <a :href="websiteUrl" target="_blank">Visit the website</a>
                            </div>
                        </div>
                    </div>
                    <div class="popup-description">
                        <slot name="description"></slot>
                    </div>
                    <div class="popup-close-button" @click="closePopup">X</div>
                </div>

            </div>

        </div>
    </div>
</template>

<style scoped>
#popup-wrapper {
  width: 100vw;
  height: 100vw;
  position: fixed;
  left: 0;
  top: 0;
  z-index: 10;
}

.popup-filter-blur {
  width: 100%;
  height: 100%;
  position: absolute;
  backdrop-filter: blur(10px);
  background-color: #00000044;
  opacity: 0.4;
  transition: opacity .4s linear;
}

.project-popup {
  width: 90vw;
  height: 90vh;
  padding: 2em 3em;
  background-color: var(--background-color);
  position: relative;
  left: 5vw;
  top: 5vh;
  z-index: 10;
  border-radius: 10px;
  transform: scale(0.4);
  opacity: 0;
  transition:
    transform .6s ease,
    opacity .6s ease;
}

.popup .popup-filter-blur {
  opacity: 1;
}

.popup .project-popup {
  transform: scale(1);
  opacity: 1;
}

.project-popup .popup-info {
  display: flex;
  margin-bottom: 1em;
}

.project-popup .popup-image {
  width: 40%;
  max-width: 400px;
}

.project-popup .popup-image img {
  width: 100%;
  height: 100%;
}

.project-popup .popup-details {
  margin-left: 1em;
}

.project-popup .popup-details h1 {
  font-size: 48px;
  font-weight: 600;
  line-height: 48px;
}

.project-popup .popup-description {
  font-weight: 400;
}

span.field-description {
  font-size: 24px;
  color: #ffffff66;
  text-transform: lowercase;
  margin-right: 5px;
}

.popup-close-button {
    position: absolute;
    right: 3rem;
    top: 2rem;
    cursor: pointer;
    font-weight: 900;
    font-size: 24px;
}

.popup-visit-button {
    background-color: #fff;
    color: var(--background-color);
    width: max-content;
    margin-top: .2em;
    cursor: pointer;
    border: 2px;
}

.popup-visit-button a {
    color: inherit;
    text-decoration: none;
    padding: .1em .5em;
    display: flex;
}

.popup-visit-button a::after {
    content: '';
    background-image: url(/src/assets/right-top-arrow.svg);
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
    width: 22px;
    height: 24px;
    display: block;
    bottom: 0;
    position: relative;
    margin-left: 0.2em;
}

@media screen and (max-width: 768px) {
    .project-popup {
        width: 100vw;
        height: 100vh;
        left: 0;
        top: 0;
        padding: 90px 1em 1em;
    }

    .project-popup .popup-info {
        flex-direction: column;
    }

    .project-popup .popup-image {
        width: 100%;
        max-width: none;
    }

    .project-popup .popup-image img {
        width: 100%;
        height: auto;
    }

    .project-popup .popup-details {
        margin-left: 0;
        margin-top: 1em;
    }
}
</style>