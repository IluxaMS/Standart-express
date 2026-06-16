<template>
    <section class="fleet-section">
        <img src="../public/decor_truck.png" alt="" class="decor decor--truck-left" />
        <img src="../public/decor_top_right.png" alt="" class="decor decor--orange-top-right" />
        <img src="../public/decor_orange_worker.png" alt="" class="decor decor--black-bottom-left" />
        <img src="../public/decor_bottom_left.png" alt="" class="decor decor--loader-right" />

        <div class="fleet-container">
            <h2 class="fleet-title">НАШ АВТОПАРК</h2>

            <div class="fleet-grid desktop-only">
                <div v-for="(car, index) in cars" :key="index" class="car-card">
                    <div class="car-image-wrapper">
                        <img :src="car.image" :alt="car.title" class="car-image" />
                    </div>

                    <h3 class="car-title">{{ car.title }}</h3>

                    <div class="car-specs">
                        <div class="spec-item">
                            <img src="../public/icon_size.png" alt="size" class="spec-icon" />
                            <div class="spec-text">
                                <span class="spec-label">Размер</span>
                                <span class="spec-value">{{ car.size }}</span>
                            </div>
                        </div>
                        <div class="spec-item">
                            <img src="../public/icon_volume.png" alt="volume" class="spec-icon" />
                            <div class="spec-text">
                                <span class="spec-label">Объем</span>
                                <span class="spec-value">{{ car.volume }}</span>
                            </div>
                        </div>
                        <div class="spec-item">
                            <img src="../public/icon_weight2.png" alt="weight" class="spec-icon" />
                            <div class="spec-text">
                                <span class="spec-label">Такелаж</span>
                                <span class="spec-value">{{ car.weight }}</span>
                            </div>
                        </div>
                    </div>

                    <p class="car-desc">{{ car.description }}</p>

                    <button class="price-btn">Узнать цену</button>
                </div>
            </div>

            <div class="carousel-wrapper mobile-only">
                <div class="carousel-viewport" ref="viewport">
                    <div class="carousel-track" :style="{
                        transform: `translateX(-${translateX}px)`,
                        transition: isTransitioning ? 'transform 0.4s ease-out' : 'none'
                    }" @transitionend="handleTransitionEnd">
                        <div v-for="(car, index) in displayCars" :key="index" class="carousel-slide"
                            :class="{ 'no-transition': !isTransitioning }" :ref="el => setSlideRef(el, index)">
                            <div class="car-card mobile-card">
                                <div class="car-image-wrapper">
                                    <img :src="car.image" :alt="car.title" class="car-image" />
                                </div>

                                <h3 class="car-title">{{ car.title }}</h3>

                                <div class="car-specs">
                                    <div class="spec-item">
                                        <img src="../public/icon_size.png" alt="size" class="spec-icon" />
                                        <div class="spec-text">
                                            <span class="spec-label">Размер</span>
                                            <span class="spec-value">{{ car.size }}</span>
                                        </div>
                                    </div>
                                    <div class="spec-item">
                                        <img src="../public/icon_volume.png" alt="volume" class="spec-icon" />
                                        <div class="spec-text">
                                            <span class="spec-label">Объем</span>
                                            <span class="spec-value">{{ car.volume }}</span>
                                        </div>
                                    </div>
                                    <div class="spec-item">
                                        <img src="../public/icon_weight2.png" alt="weight" class="spec-icon" />
                                        <div class="spec-text">
                                            <span class="spec-label">Такелаж</span>
                                            <span class="spec-value">{{ car.weight }}</span>
                                        </div>
                                    </div>
                                </div>

                                <p class="car-desc">{{ car.description }}</p>

                                <button class="price-btn">Узнать цену</button>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="carousel-controls">
                    <button class="nav-btn" @click="scroll('prev')">
                        <img src="../public/arrow_left.png" alt="<" />
                    </button>
                    <button class="nav-btn" @click="scroll('next')">
                        <img src="../public/arrow_right.png" alt=">" />
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted, nextTick } from 'vue';

import car1 from '../public/car_gazel_3m_1.png';
import car2 from '../public/car_gazel_3m_2.png';
import car3 from '../public/car_gazel_3m_3.png';
import car4 from '../public/car_gazel_3m_4.png';
import car5 from '../public/car_gazel_3m_5.png';
import car6 from '../public/car_gazel_3m_6.png';

const cars = [
    { image: car1, title: 'Газель 3-х метровая', size: '1.9х1.95х3 м', volume: '9-11м', weight: 'до 1.5 т', description: 'Газель с тентованным кузовом, одна из самых универсальных и наиболее часто заказываемых моделей нашего автопарка, которая подходит для большинства видов грузоперевозок.' },
    { image: car2, title: 'Газель 3-х метровая', size: '1.9х1.95х3 м', volume: '9-11м', weight: 'до 1.5 т', description: 'Газель с тентованным кузовом, одна из самых универсальных и наиболее часто заказываемых моделей нашего автопарка, которая подходит для большинства видов грузоперевозок.' },
    { image: car3, title: 'Газель 3-х метровая', size: '1.9х1.95х3 м', volume: '9-11м', weight: 'до 1.5 т', description: 'Газель с тентованным кузовом, одна из самых универсальных и наиболее часто заказываемых моделей нашего автопарка, которая подходит для большинства видов грузоперевозок.' },
    { image: car4, title: 'Газель 3-х метровая', size: '1.9х1.95х3 м', volume: '9-11м', weight: 'до 1.5 т', description: 'Газель с тентованным кузовом, одна из самых универсальных и наиболее часто заказываемых моделей нашего автопарка, которая подходит для большинства видов грузоперевозок.' },
    { image: car5, title: 'Газель 3-х метровая', size: '1.9х1.95х3 м', volume: '9-11м', weight: 'до 1.5 т', description: 'Газель с тентованным кузовом, одна из самых универсальных и наиболее часто заказываемых моделей нашего автопарка, которая подходит для большинства видов грузоперевозок.' },
    { image: car6, title: 'Газель 3-х метровая', size: '1.9х1.95х3 м', volume: '9-11м', weight: 'до 1.5 т', description: 'Газель с тентованным кузовом, одна из самых универсальных и наиболее часто заказываемых моделей нашего автопарка, которая подходит для большинства видов грузоперевозок.' }
];

const cloneCount = 2;
const gap = 15;
const windowWidth = ref(typeof window !== 'undefined' ? window.innerWidth : 1920);

const displayCars = computed(() => {
    return [
        ...cars.slice(-cloneCount),
        ...cars,
        ...cars.slice(0, cloneCount)
    ];
});

const slideWidth = ref(253);
const renderIndex = ref(cloneCount);
const isTransitioning = ref(true);
const isScrolling = ref(false);

const translateX = computed(() => {
    const W = windowWidth.value;
    const S = slideWidth.value;
    const G = gap;
    const step = S + G;

    const currentLeft = (renderIndex.value) * step;

    const visualOffset = 20;
    return currentLeft - visualOffset;
});

const setSlideRef = (el: any, index: number) => {
    if (el && index === 0) {
        slideWidth.value = el.offsetWidth;
    }
};

const handleTransitionEnd = () => {
    if (renderIndex.value >= cars.length + cloneCount) {
        isTransitioning.value = false;
        renderIndex.value = cloneCount;
    } else if (renderIndex.value <= cloneCount - 1) {
        isTransitioning.value = false;
        renderIndex.value = cars.length + cloneCount - 1;
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
});

onUnmounted(() => {
    window.removeEventListener('resize', handleResize);
});
</script>

<style scoped lang="scss">
.fleet-section {
    position: relative;
    width: 100%;
    min-height: 1349px;
    background-color: #F5F5F5;
    padding: 60px 0;
    overflow: hidden;
}

.decor {
    position: absolute;
    z-index: 1;
    pointer-events: none;
}

.decor--truck-left {
    top: 100px;
    left: 0;
    width: 158px;
    height: auto;
}

.decor--orange-top-right {
    top: 0;
    right: 0;
    width: 70px;
    height: auto;
}

.decor--black-bottom-left {
    bottom: 0;
    left: 0;
    width: 70px;
    height: auto;
}

.decor--loader-right {
    bottom: 100px;
    right: 0;
    width: 173px;
    height: auto;
}

.fleet-container {
    position: relative;
    z-index: 2;
    max-width: 1600px;
    margin: 0 auto;
    padding: 0 200px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.fleet-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    color: #000;
    text-transform: uppercase;
    margin: 0 0 50px 0;
    text-align: center;
}

.desktop-only {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 30px;
    width: 100%;
}

.car-card {
    background: #FFFFFF;
    border-radius: 20px;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.03);
}

.car-image-wrapper {
    width: 100%;
    height: 200px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 20px;
}

.car-image {
    max-width: 100%;
    max-height: 100%;
    object-fit: contain;
}

.car-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 20px;
    line-height: 100%;
    color: #000;
    margin: 0 0 20px 0;
}

.car-specs {
    width: 100%;
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
    padding-bottom: 20px;
    border-bottom: 1px solid #F0F0F0;
}

.spec-item {
    display: flex;
    align-items: center;
    gap: 8px;
    text-align: left;
}

.spec-icon {
    width: 30px;
    height: 30px;
    object-fit: contain;
}

.spec-text {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
}

.spec-label {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 12px;
    color: #666;
    line-height: 100%;
}

.spec-value {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 14px;
    color: #000;
    line-height: 100%;
    margin-top: 4px;
}

.car-desc {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 300;
    font-size: 14px;
    line-height: 150%;
    color: #333;
    margin: 0 0 25px 0;
    flex-grow: 1;
    text-align: left;
}

.price-btn {
    width: 100%;
    max-width: 200px;
    height: 50px;
    border-radius: 100px;
    border: 1px solid #ED9121;
    background: transparent;
    color: #ED9121;
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 14px;
    cursor: pointer;
    transition: all 0.2s;

    &:hover {
        background: #ED9121;
        color: #FFF;
    }
}

.mobile-only {
    display: none;
    width: 100%;
}

.carousel-wrapper {
    position: relative;
    width: 100%;
}

.carousel-viewport {
    width: 100%;
    overflow: hidden;
    padding: 10px 0;
}

.carousel-track {
    display: flex;
    gap: 15px;
    will-change: transform;
}

.carousel-slide {
    flex: 0 0 253px;
    width: 253px;
}

.mobile-card {
    height: 576px;
    padding: 15px;
    box-sizing: border-box;

    .car-image-wrapper {
        height: 150px;
    }

    .car-title {
        font-size: 18px;
        margin-bottom: 15px;
    }

    .car-specs {
        flex-direction: column;
        gap: 10px;
        align-items: flex-start;
        border-bottom: none;
        padding-bottom: 0;
        margin-bottom: 15px;

        .spec-item {
            width: 100%;
        }
    }

    .car-desc {
        font-size: 13px;
        margin-bottom: 20px;
    }

    .price-btn {
        max-width: 100%;
    }
}

.carousel-controls {
    display: flex;
    justify-content: center;
    gap: 20px;
    margin-top: 30px;
}

.nav-btn {
    width: 44px;
    height: 44px;
    border-radius: 50%;
    border: 1px solid #CBCBCB;
    background: #FFF;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: all 0.2s;

    img {
        width: 16px;
        height: 16px;
    }

    &:hover {
        border-color: #ED9121;
    }
}

@media (max-width: 1300px) {
    .fleet-container {
        padding: 0 40px;
    }

    .desktop-only {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (max-width: 900px) {
    .fleet-section {
        min-height: auto;
        padding: 40px 0;
    }

    .decor {
        display: none;
    }

    .fleet-container {
        padding: 0 20px;
    }

    .fleet-title {
        font-size: 32px;
        margin-bottom: 30px;
    }

    .desktop-only {
        display: none;
    }

    .mobile-only {
        display: block;
    }
}
</style>