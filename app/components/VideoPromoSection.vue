<template>
    <section class="video-promo-section">
        <div class="video-wrapper">
            <img v-if="showOverlay" src="../public/mobile_video_poster.png" alt="Preview" class="video-poster-img">

            <video ref="videoPlayer" class="video-element" preload="metadata" :controls="isPlaying" @play="handlePlay"
                @ended="handleEnded">
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

const handlePause = () => {
    isPlaying.value = false;
};

const handleEnded = () => {
    isPlaying.value = false;
    showOverlay.value = true;
};
</script>

<style scoped lang="scss">
.video-promo-section {
    width: 100%;
    padding: 40px 0;
    background-color: #F5F5F5;
    display: flex;
    justify-content: center;
}

.video-wrapper {
    position: relative;
    width: 1200px;
    height: 492px;
    max-width: 100%;
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
    margin: 0 auto;
    background-color: #000;
}

.video-poster-img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: 1;
    object-position: center;
}

.video-element {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    position: relative;
    z-index: 2;
    background-color: #000;
    opacity: 0;
    transition: opacity 0.3s ease;

    &.playing {
        opacity: 1;
    }
}

.video-element {
    opacity: 1;
}

.video-element {
    z-index: 1;
}

.video-poster-img {
    z-index: 2;
    pointer-events: none;
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
    will-change: transform;
    backface-visibility: hidden;
}

.play-circle {
    position: absolute;
    border-radius: 50%;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    backface-visibility: hidden;
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

@media (max-width: 1200px) {
    .video-wrapper {
        width: 90%;
        height: auto;
        aspect-ratio: 1200 / 492;
    }
}

@media (max-width: 1024px) {
    .video-promo-section {
        background-color: #ffffff;
        padding: 20px 0;
    }

    .video-wrapper {
        width: 342px;
        height: 252px;
        border-radius: 20px;
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
}
</style>