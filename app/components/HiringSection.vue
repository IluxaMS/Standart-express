<template>
    <section class="hiring-section">
        <div class="hiring-container">
            <div class="hiring-content">
                <img src="../public/decor_line_left.jpg" alt="" class="hero-decor hero-decor--left" />
                <h2 class="hiring-title">
                    Компания «Стандарт Экспресс» ведет набор персонала<br class="br_mob"> на частичную и полную
                    занятость
                </h2>

                <p class="hiring-subtitle">Для более подробной информации звоните по телефону:</p>

                <a href="https://wa.me/79874044157" class="whatsapp-link" target="_blank">
                    <img src="../public/whatsapp.png" alt="WhatsApp" class="whatsapp-icon" />
                    <span class="phone-number">+7 (987) 404-41-57</span>
                </a>
            </div>

            <div class="video-wrapper">
                <img v-if="showOverlay" src="../public/hiring_video_poster.png" alt="Preview" class="video-poster-img">

                <video ref="videoPlayer" class="video-element" preload="metadata" :controls="isPlaying"
                    @play="handlePlay" @ended="handleEnded">
                    <source src="../public/promo_video_1.mp4" type="video/mp4">
                </video>

                <button v-if="showOverlay" class="play-button" @click="togglePlay" aria-label="Воспроизвести видео">
                    <div class="play-animation-wrapper">
                        <span class="play-circle play-circle--outer"></span>
                        <span class="play-circle play-circle--middle"></span>
                        <span class="play-circle play-circle--inner">
                            <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
                                <path d="M8 5V19L19 12L8 5Z" fill="white" />
                            </svg>
                        </span>
                    </div>
                </button>
            </div>
        </div>
        <img src="../public/decor_line_right.jpg" alt="" class="hero-decor hero-decor--right" />
    </section>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const videoPlayer = ref<HTMLVideoElement | null>(null);
const isPlaying = ref(false);
const showOverlay = ref(true);

const togglePlay = () => {
    if (videoPlayer.value) {
        if (videoPlayer.value.paused) {
            videoPlayer.value.play();
            showOverlay.value = false;
        } else {
            videoPlayer.value.pause();
            showOverlay.value = true;
        }
    }
};

const handlePlay = () => {
    isPlaying.value = true;
    showOverlay.value = false;
};

const handleEnded = () => {
    isPlaying.value = false;
    showOverlay.value = true;
};
</script>

<style scoped lang="scss">
.hiring-section {
    width: 100%;
    background-color: #F5F5F5;
    overflow: hidden;
    position: relative;
    padding-top: 30px;
}

.hiring-container {
    max-width: 1627px;
    margin: 0 auto;
    position: relative;
    min-height: 425px;
    display: flex;
    align-items: center;
    padding-left: 200px;
    padding-right: 200px;
}

.hiring-content {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    z-index: 2;
    width: 40%;
    max-width: 600px;
    margin-top: -70px;
}

.hiring-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 40px;
    line-height: 125%;
    color: #000;
    margin: 0 0 10px 0;
    width: 110%;
    max-width: 535px;
}

.hiring-subtitle {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 100%;
    color: #000;
    margin: 0 0 15px 0;
}

.whatsapp-link {
    display: inline-flex;
    align-items: center;
    gap: 12px;
    text-decoration: none;
    transition: opacity 0.2s;

    &:hover {
        opacity: 0.8;
    }
}

.whatsapp-icon {
    width: 32px;
    height: 32px;
    object-fit: contain;
}

.phone-number {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 100%;
    color: #000;
}

.video-wrapper {
    position: absolute;
    right: 200px;
    top: 0;
    height: 100%;
    width: 610px;
    border-radius: 20px;
    overflow: hidden;
    background-color: #000;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.video-poster-img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: 2;
    pointer-events: none;
}

.video-element {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    position: relative;
    z-index: 1;
    background-color: #000;
}

.play-button {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: none;
    border: none;
    padding: 0;
    cursor: pointer;
    z-index: 10;
    width: 120px;
    height: 120px;
}

.play-animation-wrapper {
    width: 100%;
    height: 100%;
    position: relative;
    animation: pulse-animation 2s infinite ease-in-out;
}

.play-circle {
    position: absolute;
    border-radius: 50%;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.play-circle--outer {
    width: 120px;
    height: 120px;
    background-color: rgba(237, 145, 33, 0.2);
}

.play-circle--middle {
    width: 90px;
    height: 90px;
    background-color: rgba(237, 145, 33, 0.5);
}

.play-circle--inner {
    width: 60px;
    height: 60px;
    background-color: #ED9121;
    display: flex;
    align-items: center;
    justify-content: center;
}

.hero-decor--left {
    position: relative;
    width: 175px;
    height: 59px;
    right: 47%;
}

.hero-decor--right {
    position: relative;
    width: 221px;
    height: 59px;
    right: -37%;
    top: -88px;
}

.br_mob {
    display: none;
}

@keyframes pulse-animation {
    0% {
        transform: scale(0.95);
        opacity: 0.9;
    }

    50% {
        transform: scale(1.05);
        opacity: 1;
    }

    100% {
        transform: scale(0.95);
        opacity: 0.9;
    }
}

@media (max-width: 1024px) {
    .hiring-section {
        background-color: #2F2F2F;
        padding: 50px 0;
    }

    .hiring-container {
        padding: 0 20px;
        flex-direction: column;
        height: auto;
        min-height: auto;
        align-items: center;
    }

    .hiring-content {
        width: 100%;
        max-width: 100%;
        margin-bottom: 30px;
        align-items: flex-start;
        /* Выравнивание по левому краю как на скрине */
        text-align: left;
    }

    .hiring-title {
        font-size: 32px;
        color: #FFFFFF;
        margin-bottom: 20px;
        max-width: 99%;
        margin-top: 40px;
        letter-spacing: 1px;
    }

    .hiring-subtitle {
        color: #E0E0E0;
        margin-bottom: 15px;
        line-height: 20px;
        max-width: 75%;
    }

    .whatsapp-link {
        filter: invert(1);
    }

    .phone-number {
        color: #000000;
    }

    .video-wrapper {
        position: relative;
        right: auto;
        top: auto;
        width: 360px;
        height: 230px;
        border-radius: 25px;
    }

    .play-button {
        width: 60px;
        height: 60px;
    }

    .play-circle--outer {
        width: 60px;
        height: 60px;
    }

    .play-circle--middle {
        width: 45px;
        height: 45px;
    }

    .play-circle--inner {
        width: 30px;
        height: 30px;
    }

    .play-circle--inner svg {
        width: 12px;
        height: 12px;
    }

    .hero-decor {
        display: none;
    }

    .whatsapp-icon {
        filter: invert(100%);
    }

    .br_mob {
        display: block;
    }
}
</style>