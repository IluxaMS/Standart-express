<template>
    <section class="reviews-section">
        <img src="../public/reviews_bg_pattern.png" class="decor-bg" alt="">
        <img src="../public/reviews_decor_left.png" class="decor-left" alt="">
        <img src="../public/reviews_decor_right.png" class="decor-right" alt="">

        <div class="reviews-container">
            <h2 class="reviews-title">ОТЗЫВЫ</h2>
            <p class="reviews-desc">
                Грузчики от компании с опытом работы в Москве с 2013 года. Для нас ценно, что за<br class="br_mob"> это
                время <br class="br_desc">
                у нас сформировалась большая<br class="br_mob"> база постоянных клиентов,<br class="br_mob">
                рекомендующих нас другим.
            </p>

            <div class="reviews-rating">
                <img src="../public/rating_star.png" class="star-icon" alt="★">
                <span>338 оценок средняя 4,37 из 5</span>
            </div>

            <div class="reviews-tabs">
                <button v-for="tab in tabs" :key="tab.id"
                    :class="['tab-btn', { 'tab-btn--active': activeTab === tab.id }]" @click="switchTab(tab.id)">
                    {{ tab.label }}
                </button>
            </div>
        </div>

        <div class="carousel-wrapper bleed-effect" v-show="activeTab === 'audio'">
            <div class="content-limit">
                <div class="carousel-viewport">
                    <div class="carousel-track" :style="{
                        transform: `translateX(-${audioTranslateX}px)`,
                        transition: audioIsTransitioning ? 'transform 0.5s ease-in-out' : 'none'
                    }" @transitionend="handleAudioTransitionEnd">
                        <div v-for="(audio, index) in displayAudios" :key="index" class="carousel-slide audio-slide"
                            :class="{ 'is-active': index === audioRenderIndex + 1, 'no-transition': !audioIsTransitioning }"
                            :ref="el => setAudioSlideRef(el, index)">
                            <div class="audio-card-content">
                                <div class="audio-card-top">
                                    <img :src="audio.avatar" class="audio-avatar" alt="Аватар">
                                    <div class="audio-info">
                                        <p class="audio-title">
                                            <span class="audio-name">{{ audio.name }}</span>
                                            <span class="audio-dash"> - </span>
                                            <span class="audio-comment">{{ audio.text }}</span>
                                        </p>
                                    </div>
                                </div>
                                <div class="audio-card-bottom">
                                    <audio :ref="el => setAudioRef(el, index)" class="audio-element" controls
                                        @play="onAudioPlay(index)" @pause="onAudioPauseOrEnd(index)"
                                        @ended="onAudioPauseOrEnd(index)">
                                        <source :src="audio.src" type="audio/mp3">
                                    </audio>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="carousel-wrapper bleed-effect" v-show="activeTab === 'internet'">
            <div class="content-limit">
                <div class="carousel-viewport">
                    <div class="carousel-track" :style="{
                        transform: `translateX(-${internetTranslateX}px)`,
                        transition: internetIsTransitioning ? 'transform 0.5s ease-in-out' : 'none'
                    }" @transitionend="handleInternetTransitionEnd">
                        <div v-for="(item, index) in displayInternetReviews" :key="index"
                            class="carousel-slide internet-slide"
                            :class="{ 'is-active': index === internetRenderIndex + 1, 'no-transition': !internetIsTransitioning }"
                            :ref="el => setInternetSlideRef(el, index)">
                            <div class="internet-image-wrapper">
                                <img :src="item.image" :alt="item.alt" class="internet-screenshot">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="carousel-wrapper bleed-effect" v-show="activeTab === 'tenchat'">
            <div class="content-limit">
                <div class="carousel-viewport">
                    <div class="carousel-track" :style="{
                        transform: `translateX(-${tenchatTranslateX}px)`,
                        transition: tenchatIsTransitioning ? 'transform 0.5s ease-in-out' : 'none'
                    }" @transitionend="handleTenchatTransitionEnd">
                        <div v-for="(item, index) in displayTenchatReviews" :key="index"
                            class="carousel-slide tenchat-slide"
                            :class="{ 'is-active': index === tenchatRenderIndex + 1, 'no-transition': !tenchatIsTransitioning }"
                            :ref="el => setTenchatSlideRef(el, index)">
                            <div class="tenchat-image-wrapper">
                                <img :src="item.image" :alt="item.alt" class="tenchat-screenshot">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="carousel-wrapper bleed-effect" v-show="activeTab === 'yours'">
            <div class="content-limit">
                <div class="carousel-viewport">
                    <div class="carousel-track" :style="{
                        transform: `translateX(-${yoursTranslateX}px)`,
                        transition: yoursIsTransitioning ? 'transform 0.5s ease-in-out' : 'none'
                    }" @transitionend="handleYoursTransitionEnd">
                        <div v-for="(item, index) in displayYoursReviews" :key="index"
                            class="carousel-slide yours-slide"
                            :class="{ 'is-active': index === yoursRenderIndex + 1, 'no-transition': !yoursIsTransitioning }"
                            :ref="el => setYoursSlideRef(el, index)">
                            <div class="yours-card-content">
                                <div class="yours-author-block">
                                    <span class="yours-author-name">{{ item.name }}</span>
                                </div>
                                <div class="yours-text-body">
                                    {{ item.text }}
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="carousel-wrapper video-wrapper bleed-effect" v-show="activeTab === 'video'">
            <div class="carousel-viewport">
                <div class="carousel-track" :style="{
                    transform: `translateX(-${videoTranslateX}px)`,
                    transition: videoIsTransitioning ? 'transform 0.5s ease-in-out' : 'none'
                }" @transitionend="handleVideoTransitionEnd">
                    <div v-for="(video, index) in displayVideos" :key="index" class="carousel-slide video-slide"
                        :class="{ 'is-active': index === videoRenderIndex + 1, 'no-transition': !videoIsTransitioning }"
                        :ref="el => setVideoSlideRef(el, index)">
                        <div class="video-container" :class="{ 'is-playing': playingIndex === index }">
                            <video :ref="el => setVideoRef(el, index)" class="video-element" :poster="video.poster"
                                preload="metadata" :controls="isVideoActive" @pause="onVideoPauseOrEnd(index)"
                                @ended="onVideoPauseOrEnd(index)">
                                <source :src="video.src" type="video/mp4">
                            </video>
                            <div v-if="showVideoOverlay" class="video-overlay" @click="togglePlay(index)"></div>
                            <button v-if="showVideoOverlay" class="play-button" @click="togglePlay(index)">
                                <div class="play-animation-wrapper">
                                    <span class="play-circle play-circle--outer"></span>
                                    <span class="play-circle play-circle--middle"></span>
                                    <span class="play-circle play-circle--inner">
                                        <svg width="18" height="18" viewBox="0 0 24 24" fill="none">
                                            <path d="M8 5V19L19 12L8 5Z" fill="white" />
                                        </svg>
                                    </span>
                                </div>
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="reviews-container">
            <div class="carousel-controls"
                v-show="['video', 'audio', 'internet', 'tenchat', 'yours'].includes(activeTab)">
                <button class="nav-btn" @click="scroll('prev')"><img src="../public/arrow_video_left.png"
                        alt="<"></button>
                <button class="nav-btn" @click="scroll('next')"><img src="../public/arrow_video_right.png"
                        alt=">"></button>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted, nextTick, computed } from 'vue';

import video1 from '../public/promo_video_1.mp4';
import video2 from '../public/promo_video_2.mp4';
import video3 from '../public/promo_video_3.mp4';
import video4 from '../public/promo_video_4.mp4';
import video5 from '../public/promo_video_5.mp4';

import poster1 from '../public/review_poster_1.png';
import poster2 from '../public/review_poster_2.png';
import poster3 from '../public/review_poster_3.png';
import poster4 from '../public/review_poster_4.png';
import poster5 from '../public/review_poster_5.png';

import audio1 from '../public/audio_1.mp3';
import audio2 from '../public/audio_2.mp3';
import audio3 from '../public/audio_3.mp3';
import audio4 from '../public/audio_4.mp3';

import avatar1 from '../public/avatar_1.png';
import avatar2 from '../public/avatar_2.png';
import avatar3 from '../public/avatar_3.png';
import avatar4 from '../public/avatar_4.png';

import internetImg1 from '../public/internet_review_1.png';
import internetImg2 from '../public/internet_review_2.png';
import internetImg3 from '../public/internet_review_3.png';
import internetImg4 from '../public/internet_review_4.png';
import internetImg5 from '../public/internet_review_5.png';
import internetImg6 from '../public/internet_review_6.png';

import tenchatImg1 from '../public/tenchat_review_1.png';
import tenchatImg2 from '../public/tenchat_review_2.png';
import tenchatImg3 from '../public/tenchat_review_3.png';
import tenchatImg4 from '../public/tenchat_review_4.png';
import tenchatImg5 from '../public/tenchat_review_5.png';
import tenchatImg6 from '../public/tenchat_review_6.png';

const originalVideos = [
    { src: video1, poster: poster1 },
    { src: video2, poster: poster2 },
    { src: video3, poster: poster3 },
    { src: video4, poster: poster4 },
    { src: video5, poster: poster5 }
];

const originalAudios = [
    { src: audio1, avatar: avatar1, name: 'Юлия (г. Владимир)', text: 'Спасибо ребятам за переезд' },
    { src: audio2, avatar: avatar2, name: 'Руслан (г. Калининград)', text: 'Спасибо за перевозку имущества' },
    { src: audio3, avatar: avatar3, name: 'Руслан (г. Казань)', text: 'Спасибо грузчикам за работу' },
    { src: audio4, avatar: avatar4, name: 'Вадим (г. Курск)', text: 'Всё было на высшем уровне' }
];

const originalInternetReviews = [
    { image: internetImg1, alt: 'Отзыв Яндекс 1' },
    { image: internetImg2, alt: 'Отзыв Google 1' },
    { image: internetImg3, alt: 'Отзыв 2ГИС 1' },
    { image: internetImg4, alt: 'Отзыв Flamp 1' },
    { image: internetImg5, alt: 'Отзыв Otzovik 1' },
    { image: internetImg6, alt: 'Отзыв Яндекс 2' }
];

const originalTenchatReviews = [
    { image: tenchatImg1, alt: 'TenChat Отзыв 1' },
    { image: tenchatImg2, alt: 'TenChat Отзыв 2' },
    { image: tenchatImg3, alt: 'TenChat Отзыв 3' },
    { image: tenchatImg4, alt: 'TenChat Отзыв 4' },
    { image: tenchatImg5, alt: 'TenChat Отзыв 5' },
    { image: tenchatImg6, alt: 'TenChat Отзыв 6' }
];

const originalYoursReviews = [
    { text: "Хочу выразить огромную благодарность вашей компании за высокий уровень сервиса! Заказывал доставку через ваше приложение. Вся информация была предоставлена оперативно, а тарифы оказались весьма привлекательными. Особенно порадовала акция на погрузку и разгрузку. Рекомендую всем, кто ищет надежного перевозчика!", name: "Игорь" },
    { text: "Заказывали офисный переезд. Ребята приехали вовремя, упаковали всё очень бережно. Ни одной царапины на мебели. Отдельное спасибо за вежливость грузчиков.", name: "Пётр" },
    { text: "Лучшая компания в городе! Пользуюсь услугами уже третий год для перевозки товаров на маркетплейсы. Никогда не подводят со сроками.", name: "Екатерина" },
    { text: "Срочно нужно было перевезти пианино. Думал, откажут или заломят цену. Но менеджеры вошли в положение, нашли специалистов. Всё прошло идеально.", name: "Николай" },
    { text: "Честные цены, никаких скрытых доплат по окончании работ. Бригада работала слаженно, управились за 3 часа вместо заявленных 4.", name: "Александр" },
    { text: "Приятно удивлена подходом. Менеджер перезвонил через минуту после заявки. Машина была чистой, грузчики в форме. Сервис на высоте.", name: "Анна" }
];

const tabs = [
    { id: 'video', label: 'Видео отзывы' }, { id: 'audio', label: 'Аудио отзывы' },
    { id: 'internet', label: 'Отзывы из интернета' }, { id: 'tenchat', label: 'Отзывы из TenChat' },
    { id: 'yours', label: 'Ваши отзывы' }
];

const activeTab = ref('video');
const cloneCount = 3;
const gap = 20;
const windowWidth = ref(typeof window !== 'undefined' ? window.innerWidth : 1920);

const createClonedArray = (arr: any[]) => [...arr.slice(-cloneCount), ...arr, ...arr.slice(0, cloneCount)];

const videoSlideWidth = ref(0); const videoRenderIndex = ref(cloneCount); const videoIsTransitioning = ref(true); const videoIsScrolling = ref(false);
const videoRefs = ref<(HTMLVideoElement | null)[]>([]); const playingIndex = ref<number | null>(null);
const showVideoOverlay = ref(true);
const isVideoActive = ref(false);
const displayVideos = computed(() => createClonedArray(originalVideos));
const videoTranslateX = computed(() => { const W = windowWidth.value; const S = videoSlideWidth.value || 640; return ((videoRenderIndex.value + 1) * (S + gap)) - (W / 2) + (S / 2); });
const setVideoSlideRef = (el: any, i: number) => { if (el && i === 0) videoSlideWidth.value = el.offsetWidth; };
const setVideoRef = (el: any, i: number) => { if (el) videoRefs.value[i] = el; };
const togglePlay = (i: number) => {
    const p = videoRefs.value[i];
    if (!p) return;

    if (playingIndex.value !== null && playingIndex.value !== i) {
        videoRefs.value[playingIndex.value]?.pause();
    }

    if (p.paused) {
        p.play();
        showVideoOverlay.value = false;
        isVideoActive.value = true;
    } else {
        p.pause();
        showVideoOverlay.value = true;
        isVideoActive.value = false;
    }
};
const onVideoPauseOrEnd = (i: number) => {
    if (playingIndex.value === i) playingIndex.value = null;
};
const pauseAllVideos = () => { if (playingIndex.value !== null) { videoRefs.value[playingIndex.value]?.pause(); playingIndex.value = null; } };
const handleVideoTransitionEnd = () => {
    if (videoRenderIndex.value >= originalVideos.length + cloneCount) {
        videoIsTransitioning.value = false;
        videoRenderIndex.value = cloneCount;
        showVideoOverlay.value = true;
        isVideoActive.value = false;
    } else if (videoRenderIndex.value <= cloneCount - 1) {
        videoIsTransitioning.value = false;
        videoRenderIndex.value = originalVideos.length + cloneCount - 1;
        showVideoOverlay.value = true;
        isVideoActive.value = false;
    }
    videoIsScrolling.value = false;
};

const audioSlideWidth = ref(0); const audioRenderIndex = ref(cloneCount); const audioIsTransitioning = ref(true); const audioIsScrolling = ref(false);
const audioRefs = ref<(HTMLAudioElement | null)[]>([]); const playingAudioIndex = ref<number | null>(null);
const displayAudios = computed(() => createClonedArray(originalAudios));
const audioTranslateX = computed(() => { const W = windowWidth.value; const S = audioSlideWidth.value || 640; return ((audioRenderIndex.value + 1) * (S + gap)) - (W / 2) + (S / 2); });
const setAudioSlideRef = (el: any, i: number) => { if (el && i === 0) audioSlideWidth.value = el.offsetWidth; };
const setAudioRef = (el: any, i: number) => { if (el) audioRefs.value[i] = el; };
const onAudioPlay = (i: number) => { if (playingAudioIndex.value !== null && playingAudioIndex.value !== i) audioRefs.value[playingAudioIndex.value]?.pause(); playingAudioIndex.value = i; };
const onAudioPauseOrEnd = (i: number) => { if (playingAudioIndex.value === i) playingAudioIndex.value = null; };
const pauseAllAudios = () => { if (playingAudioIndex.value !== null) { audioRefs.value[playingAudioIndex.value]?.pause(); playingAudioIndex.value = null; } };
const handleAudioTransitionEnd = () => { if (audioRenderIndex.value >= originalAudios.length + cloneCount) { audioIsTransitioning.value = false; audioRenderIndex.value = cloneCount; } else if (audioRenderIndex.value <= cloneCount - 1) { audioIsTransitioning.value = false; audioRenderIndex.value = originalAudios.length + cloneCount - 1; } audioIsScrolling.value = false; };

const internetSlideWidth = ref(0); const internetRenderIndex = ref(cloneCount); const internetIsTransitioning = ref(true); const internetIsScrolling = ref(false);
const displayInternetReviews = computed(() => createClonedArray(originalInternetReviews));
const internetTranslateX = computed(() => { const W = windowWidth.value; const S = internetSlideWidth.value || 640; return ((internetRenderIndex.value + 1) * (S + gap)) - (W / 2) + (S / 2); });
const setInternetSlideRef = (el: any, i: number) => { if (el && i === 0) internetSlideWidth.value = el.offsetWidth; };
const handleInternetTransitionEnd = () => { if (internetRenderIndex.value >= originalInternetReviews.length + cloneCount) { internetIsTransitioning.value = false; internetRenderIndex.value = cloneCount; } else if (internetRenderIndex.value <= cloneCount - 1) { internetIsTransitioning.value = false; internetRenderIndex.value = originalInternetReviews.length + cloneCount - 1; } internetIsScrolling.value = false; };

const tenchatSlideWidth = ref(0); const tenchatRenderIndex = ref(cloneCount); const tenchatIsTransitioning = ref(true); const tenchatIsScrolling = ref(false);
const displayTenchatReviews = computed(() => createClonedArray(originalTenchatReviews));
const tenchatTranslateX = computed(() => { const W = windowWidth.value; const S = tenchatSlideWidth.value || 640; return ((tenchatRenderIndex.value + 1) * (S + gap)) - (W / 2) + (S / 2); });
const setTenchatSlideRef = (el: any, i: number) => { if (el && i === 0) tenchatSlideWidth.value = el.offsetWidth; };
const handleTenchatTransitionEnd = () => { if (tenchatRenderIndex.value >= originalTenchatReviews.length + cloneCount) { tenchatIsTransitioning.value = false; tenchatRenderIndex.value = cloneCount; } else if (tenchatRenderIndex.value <= cloneCount - 1) { tenchatIsTransitioning.value = false; tenchatRenderIndex.value = originalTenchatReviews.length + cloneCount - 1; } tenchatIsScrolling.value = false; };

const yoursSlideWidth = ref(0); const yoursRenderIndex = ref(cloneCount); const yoursIsTransitioning = ref(true); const yoursIsScrolling = ref(false);
const displayYoursReviews = computed(() => createClonedArray(originalYoursReviews));
const yoursTranslateX = computed(() => { const W = windowWidth.value; const S = yoursSlideWidth.value || 640; return ((yoursRenderIndex.value + 1) * (S + gap)) - (W / 2) + (S / 2); });
const setYoursSlideRef = (el: any, i: number) => { if (el && i === 0) yoursSlideWidth.value = el.offsetWidth; };
const handleYoursTransitionEnd = () => { if (yoursRenderIndex.value >= originalYoursReviews.length + cloneCount) { yoursIsTransitioning.value = false; yoursRenderIndex.value = cloneCount; } else if (yoursRenderIndex.value <= cloneCount - 1) { yoursIsTransitioning.value = false; yoursRenderIndex.value = originalYoursReviews.length + cloneCount - 1; } yoursIsScrolling.value = false; };

const updateAllSlideWidths = () => {
    const map: Record<string, { ref: any, selector: string }> = {
        video: { ref: videoSlideWidth, selector: '.video-slide' },
        audio: { ref: audioSlideWidth, selector: '.audio-slide' },
        internet: { ref: internetSlideWidth, selector: '.internet-slide' },
        tenchat: { ref: tenchatSlideWidth, selector: '.tenchat-slide' },
        yours: { ref: yoursSlideWidth, selector: '.yours-slide' }
    };
    const current = map[activeTab.value];
    if (current) {
        const el = document.querySelector(current.selector) as HTMLElement;
        if (el) current.ref.value = el.offsetWidth;
    }
};

const resetCarouselPosition = () => {
    const resets: Record<string, () => void> = {
        video: () => { videoIsTransitioning.value = false; videoRenderIndex.value = cloneCount; },
        audio: () => { audioIsTransitioning.value = false; audioRenderIndex.value = cloneCount; },
        internet: () => { internetIsTransitioning.value = false; internetRenderIndex.value = cloneCount; },
        tenchat: () => { tenchatIsTransitioning.value = false; tenchatRenderIndex.value = cloneCount; },
        yours: () => { yoursIsTransitioning.value = false; yoursRenderIndex.value = cloneCount; }
    };
    resets[activeTab.value]?.();
};

const switchTab = (id: string) => {
    pauseAllVideos();
    pauseAllAudios();
    activeTab.value = id;
    resetCarouselPosition();
    nextTick(() => {
        updateAllSlideWidths();
        resetCarouselPosition();
        setTimeout(() => {
            const maps: Record<string, { isTrans: any }> = {
                video: { isTrans: videoIsTransitioning },
                audio: { isTrans: audioIsTransitioning },
                internet: { isTrans: internetIsTransitioning },
                tenchat: { isTrans: tenchatIsTransitioning },
                yours: { isTrans: yoursIsTransitioning }
            };
            if (maps[id]) maps[id].isTrans.value = true;
        }, 50);
    });
};

const scroll = (dir: 'prev' | 'next') => {
    const actions: Record<string, { isScrolling: any, isTrans: any, inc: () => void, dec: () => void, pause?: () => void }> = {
        video: { isScrolling: videoIsScrolling, isTrans: videoIsTransitioning, inc: () => videoRenderIndex.value++, dec: () => videoRenderIndex.value--, pause: pauseAllVideos },
        audio: { isScrolling: audioIsScrolling, isTrans: audioIsTransitioning, inc: () => audioRenderIndex.value++, dec: () => audioRenderIndex.value--, pause: pauseAllAudios },
        internet: { isScrolling: internetIsScrolling, isTrans: internetIsTransitioning, inc: () => internetRenderIndex.value++, dec: () => internetRenderIndex.value-- },
        tenchat: { isScrolling: tenchatIsScrolling, isTrans: tenchatIsTransitioning, inc: () => tenchatRenderIndex.value++, dec: () => tenchatRenderIndex.value-- },
        yours: { isScrolling: yoursIsScrolling, isTrans: yoursIsTransitioning, inc: () => yoursRenderIndex.value++, dec: () => yoursRenderIndex.value-- }
    };
    const act = actions[activeTab.value];
    if (!act || act.isScrolling.value) return;
    act.isScrolling.value = true; act.isTrans.value = true; act.pause?.();
    dir === 'next' ? act.inc() : act.dec();
};

const handleResize = () => { windowWidth.value = window.innerWidth; updateAllSlideWidths(); };
onMounted(() => {
    nextTick(() => {
        updateAllSlideWidths();
        resetCarouselPosition();
    });
    window.addEventListener('resize', handleResize);
});
onUnmounted(() => window.removeEventListener('resize', handleResize));
</script>

<style scoped lang="scss">
.reviews-section {
    position: relative;
    width: 100%;
    padding: 80px 0;
    background-color: #212121;
    overflow-x: hidden;
    overflow-y: visible;
    z-index: 1;
    font-family: "Euclid Circular A", sans-serif;
}

.decor-bg {
    width: 100%;
    height: 100%;
    object-fit: cover;
    position: absolute;
    top: 0;
    left: 0;
    pointer-events: none;
    z-index: -1;
}

.decor-left {
    position: absolute;
    bottom: 0%;
    left: 28%;
    max-width: 15%;
    pointer-events: none;
    z-index: 0;
}

.decor-right {
    position: absolute;
    top: 0%;
    right: 22%;
    max-width: 15%;
    pointer-events: none;
    z-index: 3;
}

.reviews-container {
    max-width: 1400px;
    margin: 0 auto;
    padding: 0 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    z-index: 4;
}

.reviews-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 42px;
    color: #FFFFFF;
    margin-bottom: 20px;
    text-align: center;
    text-transform: uppercase;
}

.reviews-desc {
    font-family: "Euclid Circular A", sans-serif;
    font-size: 16px;
    color: #E0E0E0;
    margin-bottom: 24px;
    max-width: 800px;
    text-align: center;
    line-height: 1.4;
}

.reviews-rating {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    color: #FFFFFF;
    margin-bottom: 40px;
    font-size: 16px;
}

.star-icon {
    width: 20px;
    height: 20px;
}

.reviews-tabs {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 25px;
    margin-bottom: 50px;
    width: 100%;
}

.tab-btn {
    background: none;
    border: none;
    padding: 0 0 4px 0;
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 500;
    font-size: 16px;
    color: #FFFFFF;
    cursor: pointer;
    border-bottom: 1px dashed #FFFFFF;
    transition: all 0.3s ease;

    &--active {
        color: #ED9121;
        border-bottom-color: transparent;
    }

    &:hover {
        color: #ED9121;
        border-bottom-color: transparent;
    }
}

.carousel-wrapper {
    position: relative;
    width: 100%;
    display: flex;
    justify-content: center;
}

.content-limit {
    max-width: 1670px;
    width: 100%;
    margin: 0 auto;
    padding: 0 40px;
    box-sizing: border-box;
    overflow: visible;
}

.carousel-viewport {
    width: 100%;
    overflow: visible;
    padding: 20px 0;
}

.carousel-track {
    display: flex;
    gap: 20px;
    will-change: transform;
}

.carousel-slide {
    width: 640px;
    flex: 0 0 640px;
    transition: transform 0.5s ease-in-out, opacity 0.5s ease-in-out, box-shadow 0.5s ease-in-out;
    transform-origin: center;
    transform: scale(0.9);

    &.no-transition {
        transition: none !important;
    }

    &.is-active {
        opacity: 1;
        transform: scale(1.05);
        z-index: 2;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
    }
}

.video-slide {
    height: auto;
    aspect-ratio: 504 / 285.32;
    border-radius: 20px;
    overflow: hidden;
    background-color: #222;
}

.video-container {
    position: relative;
    width: 100%;
    height: 100%;
    border-radius: 20px;
    overflow: hidden;
}

.video-overlay {
    position: absolute;
    inset: 0;
    background: rgba(0, 0, 0, 0.45);
    z-index: 2;
    cursor: pointer;
    transition: opacity 0.3s;
}

.is-playing .video-overlay {
    opacity: 0;
    pointer-events: none;
}

.video-element {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
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
    width: 90px;
    height: 90px;
}

.play-animation-wrapper {
    width: 100%;
    height: 100%;
    position: relative;
    animation: pulse 2s infinite ease-in-out;
}

.play-circle {
    position: absolute;
    border-radius: 50%;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.play-circle--outer {
    width: 90px;
    height: 90px;
    background: rgba(237, 145, 33, 0.2);
}

.play-circle--middle {
    width: 70px;
    height: 70px;
    background: rgba(237, 145, 33, 0.5);
}

.play-circle--inner {
    width: 48px;
    height: 48px;
    background: #ED9121;
    display: flex;
    align-items: center;
    justify-content: center;
}

@keyframes pulse {

    0%,
    100% {
        transform: scale(0.95);
        opacity: 0.9;
    }

    50% {
        transform: scale(1.05);
        opacity: 1;
    }
}

.audio-slide {
    background-color: #FFFFFF;
    border-radius: 20px;
    padding: 24px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 190px;
    box-sizing: border-box;

    &.is-active {
        background-color: #FFFFFF;
    }
}

.audio-card-content {
    display: flex;
    flex-direction: column;
    height: 100%;
    justify-content: space-between;
}

.audio-card-top {
    display: flex;
    align-items: center;
    gap: 16px;
}

.audio-avatar {
    width: 70px;
    height: 70px;
    border-radius: 8px;
    object-fit: cover;
}

.audio-info {
    flex: 1;
}

.audio-title {
    font-family: "Euclid Circular A", sans-serif;
    font-size: 15px;
    color: #000000;
    margin: 0;
    line-height: 1.3;
}

.audio-name {
    font-weight: 700;
}

.audio-element {
    width: 100%;
    height: 40px;
    margin-top: 10px;
    border-radius: 10px;
}

.internet-slide {
    background-color: #FFFFFF;
    border-radius: 20px;
    padding: 10px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 350px;
    box-sizing: border-box;
    overflow: hidden;
}

.tenchat-slide {
    background-color: #FFFFFF;
    border-radius: 20px;
    padding: 10px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 550px;
    box-sizing: border-box;
    overflow: hidden;
}

.internet-image-wrapper,
.tenchat-image-wrapper {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #f5f5f5;
    border-radius: 12px;
    overflow: hidden;
}

.internet-screenshot,
.tenchat-screenshot {
    width: 100%;
    height: 100%;
    object-fit: contain;
    display: block;
}

.yours-slide {
    background-color: #BCBCBC;
    border-radius: 20px;
    padding: 40px;
    padding-top: 30px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    height: 250px;
    box-sizing: border-box;

    &.is-active {
        background-color: #FFFFFF;
    }
}

.yours-card-content {
    display: flex;
    flex-direction: column;
    height: 100%;
    justify-content: space-between;
}

.yours-text-body {
    font-family: "Euclid Circular A", sans-serif;
    font-size: 18px;
    line-height: 1.6;
    color: #000000;
    margin-bottom: 30px;
    flex-grow: 1;
}

.yours-author-block {
    display: flex;
    flex-direction: column;
    gap: 6px;
    margin-bottom: 15px;
}

.yours-author-name {
    font-weight: 700;
    font-size: 18px;
    color: #000000;
}

.yours-source {
    font-size: 15px;
    color: #666666;
    font-weight: 500;
}

.carousel-controls {
    display: flex;
    gap: 10px;
    margin-top: 40px;
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

.br_mob {
    display: none;
}

@media (max-width: 1400px) {
    .carousel-slide {
        width: 500px;
        flex: 0 0 500px;
    }

    .internet-slide,
    .tenchat-slide,
    .yours-slide {
        height: 450px;
    }
}

@media (max-width: 1024px) {
    .carousel-slide {
        width: 400px;
        flex: 0 0 400px;
    }

    .internet-slide,
    .tenchat-slide,
    .yours-slide {
        height: 400px;
        padding: 20px;
    }

    .content-limit {
        padding: 0 20px;
    }
}

@media (max-width: 768px) {
    .reviews-section {
        padding: 40px 0;
        background-color: #1A1A1A;
    }

    .reviews-container {
        padding: 0 20px;
        align-items: center;
    }

    .reviews-title {
        font-size: 32px;
        margin-bottom: 15px;
        text-align: left;
    }

    .reviews-desc {
        font-size: 14px;
        line-height: 1.4;
        margin-bottom: 20px;
        text-align: center;
        max-width: 94%;
    }

    .reviews-rating {
        justify-content: flex-start;
        margin-bottom: 30px;
        font-size: 14px;
    }

    .star-icon {
        width: 16px;
        height: 16px;
    }

    .reviews-tabs {
        display: flex;
        flex-direction: row;
        align-items: center;
        gap: 8px;
        margin-bottom: 40px;
        width: 115%;
    }

    .tab-btn {
        font-size: 13px;
        padding: 0;
        max-width: 70px;
        text-align: center;
        padding-bottom: 7px;
    }

    .content-limit {
        padding: 0;
        overflow: hidden;
    }

    .carousel-viewport {
        overflow: visible;
        padding: 10px 0;
    }

    .carousel-track {
        gap: 15px;
        padding-left: 20px;
    }

    .carousel-slide {
        flex: 0 0 85vw !important;
        width: 85vw !important;
        max-width: 340px;
        transform: scale(1) !important;
        opacity: 1 !important;
        box-shadow: none !important;
    }

    .video-slide {
        aspect-ratio: 16 / 9;
        height: auto !important;
    }

    .audio-slide {
        height: 160px !important;
        padding: 15px !important;
    }

    .internet-slide,
    .tenchat-slide,
    .yours-slide {
        height: 280px !important;
        padding: 10px !important;
    }

    .yours-text-body {
        font-size: 14px;
        line-height: 1.4;
    }

    .audio-avatar {
        width: 50px;
        height: 50px;
    }

    .audio-title {
        font-size: 13px;
    }

    .carousel-controls {
        margin-top: 30px;
        gap: 15px;
    }

    .decor-left,
    .decor-right {
        display: none;
    }

    @keyframes mobile-carousel-fix {
        from {
            transform: translateX(0);
        }

        to {
            transform: translateX(0);
        }
    }

    .carousel-track {
        animation: mobile-carousel-fix 0.01s ease-in-out;
    }

    .br_desc {
        display: none;
    }

    .br_mob {
        display: block;
    }
}
</style>