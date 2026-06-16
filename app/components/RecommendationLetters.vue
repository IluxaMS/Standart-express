<template>
    <section class="recommendation-section">
        <img src="../public/bg-pattern.png" alt="" class="bg-pattern" />
        <img src="../public/decor_line_left.png" alt="" class="decor-line-left" />
        <img src="../public/decor_line_right.png" alt="" class="decor-line-right" />
        <img src="../public/decor-cubes.png" alt="" class="decor-cubes" />

        <div class="recommendation-container">
            <h2 class="recommendation-title">
                РЕКОМЕНДАТЕЛЬНЫЕ ПИСЬМА<br />ОТ КРУПНЫХ КЛИЕНТОВ
            </h2>

            <div class="carousel-wrapper">
                <div class="carousel-viewport">
                    <div class="carousel-track" :style="{
                        transform: `translateX(-${translateX}px)`,
                        transition: isTransitioning ? 'transform 0.5s ease-in-out' : 'none'
                    }" @transitionend="handleTransitionEnd">
                        <div v-for="(item, index) in displayItems" :key="index" class="carousel-slide"
                            :class="{ 'no-transition': !isTransitioning }" :ref="el => setSlideRef(el, index)">
                            <div class="letter-card" @click="openLightbox(index)">
                                <img :src="item.src" :alt="item.alt" class="letter-image" />
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="carousel-controls">
                <button class="nav-btn" @click="scroll('prev')">
                    <img src="../public/arrow_video_left.png" alt="<" />
                </button>
                <button class="nav-btn" @click="scroll('next')">
                    <img src="../public/arrow_video_right.png" alt=">" />
                </button>
            </div>
        </div>

        <transition name="lightbox-fade">
            <div v-if="isLightboxOpen" class="lightbox-overlay" @click.self="closeLightbox">
                <button class="lightbox-close" @click="closeLightbox">
                    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <path d="M18 6L6 18M6 6l12 12" />
                    </svg>
                </button>

                <button class="lightbox-nav lightbox-prev" @click="scroll('prev')">
                    <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <path d="M15 18l-6-6 6-6" />
                    </svg>
                </button>

                <div class="lightbox-content">
                    <img :src="currentLetter.src" :alt="currentLetter.alt" class="lightbox-image" />
                    <p class="lightbox-caption">{{ currentLetter.alt }}</p>
                </div>

                <button class="lightbox-nav lightbox-next" @click="scroll('next')">
                    <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <path d="M9 18l6-6-6-6" />
                    </svg>
                </button>
            </div>
        </transition>
    </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted, nextTick, computed } from 'vue';

import mtsLetter from '../public/mts_letter.png';
import pacLetter from '../public/pac_letter.png';
import avitoLetter from '../public/avito_letter.png';
import businessLinesLetter from '../public/business_lines_letter.png';
import beelineLetter from '../public/beeline_letter.png';
import ubsLetter from '../public/ubs_letter.png';
import intasLetter from '../public/intas_letter.png';
import nordaTransLetter from '../public/norda_trans_letter.png';

const originalLetters = [
    { src: mtsLetter, alt: 'Письмо МТС' },
    { src: pacLetter, alt: 'Письмо ПЭК' },
    { src: avitoLetter, alt: 'Письмо Avito' },
    { src: businessLinesLetter, alt: 'Письмо Деловые линии' },
    { src: beelineLetter, alt: 'Письмо Билайн' },
    { src: ubsLetter, alt: 'Письмо ЮБС' },
    { src: intasLetter, alt: 'Письмо Intas' },
    { src: nordaTransLetter, alt: 'Письмо Norda Trans' }
];

const cloneCount = 4;
const gap = 23;
const windowWidth = ref(typeof window !== 'undefined' ? window.innerWidth : 1920);

const slideWidth = ref(224);
const renderIndex = ref(cloneCount);
const isTransitioning = ref(true);
const isScrolling = ref(false);

const isLightboxOpen = ref(false);

const currentLetter = computed(() => {
    return displayItems.value[renderIndex.value] || originalLetters[0];
});

const displayItems = computed(() => {
    return [
        ...originalLetters.slice(-cloneCount),
        ...originalLetters,
        ...originalLetters.slice(0, cloneCount)
    ];
});

const translateX = computed(() => {
    const W = windowWidth.value;
    const S = slideWidth.value || 224;
    const G = gap;
    const step = S + G;
    const activeLeftOnTrack = (renderIndex.value + 1) * step;
    const centerOffset = (W / 2) - (S / 2);
    return activeLeftOnTrack - centerOffset;
});

const setSlideRef = (el: any, index: number) => {
    if (el && index === 0) slideWidth.value = el.offsetWidth;
};

const handleTransitionEnd = () => {
    if (renderIndex.value >= originalLetters.length + cloneCount) {
        isTransitioning.value = false;
        renderIndex.value = cloneCount;
    } else if (renderIndex.value <= cloneCount - 1) {
        isTransitioning.value = false;
        renderIndex.value = originalLetters.length + cloneCount - 1;
    }
    isScrolling.value = false;
};

const scroll = (direction: 'prev' | 'next') => {
    if (isScrolling.value) return;
    isScrolling.value = true;
    isTransitioning.value = true;

    if (direction === 'next') renderIndex.value++;
    else renderIndex.value--;
};


const openLightbox = (index: number) => {
    isLightboxOpen.value = true;
    document.body.style.overflow = 'hidden';
};

const closeLightbox = () => {
    isLightboxOpen.value = false;
    document.body.style.overflow = '';
};

const handleKeydown = (e: KeyboardEvent) => {
    if (!isLightboxOpen.value) return;
    if (e.key === 'Escape') closeLightbox();
    if (e.key === 'ArrowRight') scroll('next');
    if (e.key === 'ArrowLeft') scroll('prev');
};

const handleResize = () => {
    windowWidth.value = window.innerWidth;
    nextTick(() => {
        const firstSlide = document.querySelector('.carousel-slide') as HTMLElement;
        if (firstSlide) slideWidth.value = firstSlide.offsetWidth;
    });
};

onMounted(() => {
    nextTick(() => {
        const firstSlide = document.querySelector('.carousel-slide') as HTMLElement;
        if (firstSlide) slideWidth.value = firstSlide.offsetWidth;
        isTransitioning.value = false;
        renderIndex.value = cloneCount;
        setTimeout(() => { isTransitioning.value = true; }, 50);
    });
    window.addEventListener('resize', handleResize);
    window.addEventListener('keydown', handleKeydown);
});

onUnmounted(() => {
    window.removeEventListener('resize', handleResize);
    window.removeEventListener('keydown', handleKeydown);
    document.body.style.overflow = '';
});
</script>

<style scoped lang="scss">
.recommendation-section {
    position: relative;
    width: 100%;
    min-height: 672px;
    background-color: #1A1A1A;
    overflow: hidden;
    font-family: "Euclid Circular A", sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
}

.bg-pattern {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    pointer-events: none;
    z-index: 0;
}

.decor-line-left {
    position: absolute;
    left: 0%;
    top: 75%;
    transform: translateY(-50%);
    width: 221px;
    height: 60px;
    pointer-events: none;
    z-index: 1;
}

.decor-line-right {
    position: absolute;
    right: 0%;
    top: 10%;
    transform: translateY(10%);
    width: 220px;
    height: 60px;
    pointer-events: none;
    z-index: 1;
}

.decor-cubes {
    position: absolute;
    right: 46px;
    bottom: 46px;
    width: 90px;
    height: 85px;
    pointer-events: none;
    z-index: 1;
}

.recommendation-container {
    position: relative;
    z-index: 2;
    width: 100%;
    max-width: 1600px;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0 40px;
}

.recommendation-title {
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    text-transform: uppercase;
    color: #FFFFFF;
    margin: 0 0 60px 0;
    text-align: center;
    white-space: pre-line;
}

.carousel-wrapper {
    position: relative;
    width: 100%;
    display: flex;
    justify-content: center;
}

.carousel-viewport {
    width: 65%;
    overflow: hidden;
    padding: 20px 0;
}

.carousel-track {
    display: flex;
    gap: 28px;
    will-change: transform;
    margin: 0;
}

.carousel-slide {
    width: 224px;
    flex: 0 0 224px;
    transition: transform 0.5s ease-in-out;

    &.no-transition {
        transition: none !important;
    }
}

.letter-card {
    width: 100%;
    height: auto;
    border: 8px solid #4C4C4C;
    background-color: #FFFFFF;
    box-sizing: border-box;
    overflow: hidden;
    border-radius: 4px;
    cursor: pointer;
    transition: transform 0.3s ease, border-color 0.3s ease;

    &:hover {
        transform: scale(1.02);
        border-color: #ED9121;
    }

    &:hover .letter-image {
        filter: grayscale(0%);
    }
}

.letter-image {
    width: 100%;
    height: auto;
    display: block;
    aspect-ratio: 224 / 302;
    object-fit: cover;
    filter: grayscale(100%);
    transition: filter 0.3s ease;
}

.carousel-controls {
    display: flex;
    gap: 10px;
    margin-top: 50px;
    justify-content: center;
}

.nav-btn {
    background: #1c1c1e;
    border: 1px solid #3a3a3c;
    border-radius: 50%;
    width: 50px;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: all 0.2s;

    &:hover {
        border-color: #ED9121;
    }

    img {
        width: 50px;
        height: 50px;
        object-fit: contain;
    }
}

.lightbox-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: rgba(10, 10, 10, 0.95);
    z-index: 9999;
    display: flex;
    align-items: center;
    justify-content: center;
    backdrop-filter: blur(5px);
}

.lightbox-content {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 90vw;
    max-height: 90vh;
}

.lightbox-image {
    width: 488px;
    height: 638px;
    object-fit: contain;
    border: 8px solid #4C4C4C;
    background: #fff;
    box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
    max-width: 100%;
    max-height: 80vh;
    height: auto;
    aspect-ratio: 488/638;
}

.lightbox-caption {
    color: #fff;
    margin-top: 15px;
    font-size: 16px;
    opacity: 0.8;
}

.lightbox-close {
    position: absolute;
    top: 30px;
    right: 30px;
    background: none;
    border: none;
    color: #fff;
    cursor: pointer;
    padding: 10px;
    transition: transform 0.2s;
    z-index: 10000;

    &:hover {
        transform: scale(1.1);
        color: #ED9121;
    }
}

.lightbox-nav {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(255, 255, 255, 0.1);
    border: 1px solid rgba(255, 255, 255, 0.2);
    border-radius: 50%;
    width: 60px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #fff;
    cursor: pointer;
    transition: all 0.2s;
    z-index: 10000;

    &:hover {
        background: #ED9121;
        border-color: #ED9121;
    }
}

.lightbox-prev {
    left: 40px;
}

.lightbox-next {
    right: 40px;
}

.lightbox-fade-enter-active,
.lightbox-fade-leave-active {
    transition: opacity 0.3s ease;
}

.lightbox-fade-enter-from,
.lightbox-fade-leave-to {
    opacity: 0;
}

/* Адаптив */
@media (max-width: 768px) {
    .recommendation-section {
        min-height: auto;
        padding: 40px 0;
    }

    .recommendation-title {
        font-size: 26px;
        line-height: 33px;
        margin-bottom: 25px;

        br {
            display: none;
        }
    }

    .decor-cubes,
    .decor-line-left,
    .decor-line-right {
        display: none;
    }

    .recommendation-container {
        padding: 0 20px;
    }

    .carousel-viewport {
        width: 100%;
        overflow: hidden;
        padding: 0;
    }

    .carousel-track {
        gap: 15px !important;
        padding-left: 20px !important;
    }

    .carousel-slide {
        flex: 0 0 220px !important;
        width: 220px !important;

        .letter-card {
            height: 302px;

            .letter-image {
                height: 100%;
                aspect-ratio: auto;
            }
        }
    }
}
</style>