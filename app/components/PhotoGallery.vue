<template>
    <section class="photo-gallery">
        <div class="gallery-container">
            <h2 class="gallery-title">ФОТОГАЛЕРЕЯ</h2>

            <div class="carousel-wrapper">
                <div class="carousel-viewport" ref="viewport">
                    <div class="carousel-track" :style="{
                        transform: `translateX(-${(renderIndex * (slideWidth + gap)) + (0.7 * slideWidth)}px)`,
                        transition: isTransitioning ? 'transform 0.5s ease-in-out' : 'none'
                    }" @transitionend="handleTransitionEnd">
                        <div v-for="(photo, index) in displayPhotos" :key="index" class="carousel-slide"
                            :ref="el => setSlideRef(el, index)">
                            <img :src="photo" :alt="`Фото`">
                        </div>
                    </div>
                </div>
            </div>

            <div class="carousel-controls">
                <button class="nav-btn" @click="scroll('prev')">
                    <img src="../public/arrow_left.png" alt="<">
                </button>
                <button class="nav-btn" @click="scroll('next')">
                    <img src="../public/arrow_right.png" alt=">">
                </button>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted, nextTick, computed } from 'vue';

import gallery1 from '../public/gallery_1.png';
import gallery2 from '../public/gallery_2.png';
import gallery3 from '../public/gallery_3.png';
import gallery4 from '../public/gallery_4.png';
import gallery5 from '../public/gallery_5.png';
import gallery6 from '../public/gallery_6.png';
import gallery7 from '../public/gallery_7.png';
import gallery8 from '../public/gallery_8.png';

const originalPhotos = [
    gallery1, gallery2, gallery3, gallery4,
    gallery5, gallery6, gallery7, gallery8
];

const cloneCount = 4;

const displayPhotos = computed(() => {
    return [
        ...originalPhotos.slice(-cloneCount),
        ...originalPhotos,
        ...originalPhotos.slice(0, cloneCount)
    ];
});

const viewport = ref<HTMLDivElement | null>(null);
const slideWidth = ref(0);
const gap = 20;

const renderIndex = ref(cloneCount);
const isTransitioning = ref(true);
const isScrolling = ref(false);

const setSlideRef = (el: any, index: number) => {
    if (el && index === 0) {
        slideWidth.value = el.offsetWidth;
    }
};

const updateSlideWidth = () => {
    const firstSlide = document.querySelector('.carousel-slide') as HTMLElement;
    if (firstSlide) {
        slideWidth.value = firstSlide.offsetWidth;
    }
};

const scroll = (direction: 'prev' | 'next') => {
    if (isScrolling.value) return;
    isScrolling.value = true;
    isTransitioning.value = true;

    if (direction === 'next') {
        renderIndex.value++;
    } else {
        renderIndex.value--;
    }
};

const handleTransitionEnd = () => {
    if (renderIndex.value >= originalPhotos.length + cloneCount) {
        isTransitioning.value = false;
        renderIndex.value = cloneCount;
    }
    else if (renderIndex.value <= cloneCount - 1) {
        isTransitioning.value = false;
        renderIndex.value = originalPhotos.length + cloneCount - 1;
    }
    isScrolling.value = false;
};

onMounted(() => {
    nextTick(() => {
        updateSlideWidth();
    });
    window.addEventListener('resize', updateSlideWidth);
});

onUnmounted(() => {
    window.removeEventListener('resize', updateSlideWidth);
});
</script>

<style scoped lang="scss">
.photo-gallery {
    width: 100%;
    padding: 60px 0;
    background-color: #F9F9F9;
    overflow: hidden;
}

.gallery-container {
    max-width: 1400px;
    margin: 0 auto;
    padding: 0 60px;
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.gallery-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    text-transform: uppercase;
    text-align: center;
    margin-bottom: 40px;
    color: #000;
}

.carousel-wrapper {
    position: relative;
    width: 100%;
    display: flex;
    justify-content: center;
}

.carousel-viewport {
    --visible-slides: 3;
    width: 100%;
    overflow: hidden;
    scrollbar-width: none;

    &::-webkit-scrollbar {
        display: none;
    }
}

.carousel-track {
    display: flex;
    gap: 20px;
    will-change: transform;
}

.carousel-slide {
    flex: 0 0 calc((100% - (var(--visible-slides) * 20px)) / var(--visible-slides));
    height: 400px;
    border-radius: 20px;
    overflow: hidden;
    background-color: #fff;

    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        display: block;
    }
}

.carousel-controls {
    display: flex;
    gap: 15px;
    margin-top: 30px;
    justify-content: center;
}

.nav-btn {
    background: #FFFFFF;
    border: 1px solid #E0E0E0;
    border-radius: 50%;
    width: 50px;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: all 0.2s;

    &:hover {
        transform: scale(1.1);
    }

    img {
        width: 50px;
        height: 50px;
        object-fit: contain;
    }
}

@media (max-width: 1300px) {
    .carousel-slide {
        height: 300px;
    }
}

@media (max-width: 768px) {
    .photo-gallery {
        padding: 40px 0;
    }

    .gallery-container {
        padding: 0 20px;
    }

    .gallery-title {
        font-size: 26px;
        margin-bottom: 30px;
    }

    .carousel-viewport {
        --visible-slides: 1;
        width: 100%;
        overflow: visible;
    }

    .carousel-track {
        gap: 15px;
        padding-left: 20px;
    }

    .carousel-slide {
        flex: 0 0 225px !important;
        width: 225px !important;
        height: 168px;
        border-radius: 16px;

        img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 16px;
        }
    }

    .carousel-controls {
        margin-top: 25px;
        gap: 20px;
    }

    .nav-btn {
        width: 44px;
        height: 44px;
    }
}
</style>