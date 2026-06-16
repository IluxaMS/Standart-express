<template>
    <section class="hero-section">
        <div class="hero-container">
            <img src="../public/decor_line_left.jpg" alt="" class="hero-decor hero-decor--left" />
            <div class="hero-content">
                <div class="hero-title-row">
                    <h1 class="hero-title">
                        {{ props.titleLine1 }}
                        <br v-if="props.showBrDesc" class="br_desc" />
                        {{ props.titleLine2 }}
                        <br v-if="props.showBrMob" class="br_mob" />
                        {{ props.titleLine3 }}
                        <div class="hero-price-tag">{{ props.titleLine4 }}</div>
                    </h1>
                </div>
                <p class="hero-subtitle">{{ props.titleLine5 }}</p>
                <AdvantagesSection class="mobile-only" />
                <button id="scroll-to-calculator" class="hero-button">
                    <img src="../public/calc_icon.png" alt="calc" class="hero-button-icon" />
                    Рассчитать стоимость
                </button>
            </div>
            <div class="hero-image-wrapper">
                <img :src="props.heroImageSrc" :alt="props.heroImageAlt" class="hero-image" />
            </div>
            <img src="../public/decor_line_right.jpg" alt="" class="hero-decor hero-decor--right" />
        </div>
    </section>
</template>

<script setup lang="ts">
import AdvantagesSection from './AdvantagesSection.vue'

interface Props {
    titleLine1?: string;
    titleLine2?: string;
    titleLine3?: string;
    titleLine4?: string;
    titleLine5?: string;
    heroImageSrc?: string;
    heroImageAlt?: string;
    showBrDesc?: boolean;
    showBrMob?: boolean;
}

const props = withDefaults(defineProps<Props>(), {
    titleLine1: 'Услуги грузчиков',
    titleLine2: 'в Москве',
    heroImageSrc: '../public/warehouse_worker.jpg',
    heroImageAlt: 'Грузчик на складе',
    showBrDesc: true,
    showBrMob: false
});

</script>

<style scoped lang="scss">
.mobile-only {
    display: none;
}

.hero-section {
    width: 100%;
    background-color: #ffffff;
    overflow: hidden;
    position: relative;
}

.hero-container {
    max-width: 1627px;
    margin: 0 auto;
    position: relative;
    min-height: 425px;
    display: flex;
    align-items: center;
    padding-left: 200px;
    padding-right: 200px;
}

.hero-content {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    z-index: 2;
    width: 46%;
    max-width: 600px;
}

.hero-title-row {
    display: flex;
    align-items: center;
    gap: 15px;
    margin-bottom: 20px;
}

.hero-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 50px;
    line-height: 120%;
    color: #000;
    margin: 0;
    width: 100%;
}

.hero-price-tag {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    background-color: #ed9121;
    color: #ffffff;
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 32px;
    line-height: 100%;
    border-radius: 100px;
    padding: 11px 18px;
    white-space: nowrap;
}

.hero-subtitle {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 170%;
    color: #000;
    margin: 0;
    margin-bottom: 20px;
    max-width: 413px;
    text-align: left;
}

.hero-button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    background-color: #000;
    color: #ffffff;
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 18px;
    line-height: 100%;
    border-radius: 100px;
    padding: 20px 30px;
    border: none;
    cursor: pointer;
    transition: all 0.2s ease-in-out;

    &:hover {
        background-color: #ed9121;
    }

    &:active {
        transform: scale(0.96);
    }
}

.hero-button-icon {
    width: 17.5px;
    height: 20px;
    object-fit: contain;
}

.hero-image-wrapper {
    position: absolute;
    right: 200px;
    top: 0;
    height: 100%;
    width: 610px;
    display: flex;
    align-items: center;
}

.hero-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 20px;
}

.hero-decor {
    position: absolute;
    z-index: 1;
    opacity: 1;
    pointer-events: none;
}

.hero-decor--left {
    top: 80px;
    left: -19px;
    width: 180px;
}

.hero-decor--right {
    top: 285px;
    left: 587px;
    width: 230px;
}

.br_mob {
    display: none;
}

@media (max-width: 1024px) {
    .mobile-only {
        display: block;
        margin: 30px 0;
        margin-top: 0px;
        width: 100%;
    }

    .hero-section {
        background-color: #2f2f2f;
    }

    .hero-container {
        padding: 40px 20px;
        padding-top: 25px;
        flex-direction: column;
        height: auto;
        min-height: auto;
    }

    .hero-content {
        width: 100%;
        max-width: 100%;
        margin-bottom: 30px;
        align-items: center;
        text-align: center;
    }

    .hero-title-row {
        flex-direction: row;
        gap: 10px;
        margin-bottom: 15px;
        width: 105%;
    }

    .hero-title {
        font-size: 32px;
        line-height: 1.4;
        width: 100%;
        margin: 0;
        color: #ffffff;
        text-align: left;
    }

    .hero-price-tag {
        font-size: 32px;
        padding: 8px 16px;
        align-self: center;
    }

    .hero-subtitle {
        margin-top: 15px;
        margin-bottom: 20px;
        margin-right: 18px;
        color: #ffffff;
        width: 102%;
    }

    .hero-button {
        width: 93%;
        font-size: 16px;
        padding: 18px 20px;
        background-color: #ed9121;

        &:hover {
            background-color: #d67e16;
        }
    }

    .hero-button-icon {
        filter: brightness(0) invert(1);
    }

    .hero-image-wrapper {
        position: relative;
        right: auto;
        top: auto;
        width: 100%;
        height: auto;
        aspect-ratio: 343 / 220;
    }

    .hero-image {
        border-radius: 12px;
        width: 100%;
        height: 100%;
    }

    .hero-decor,
    .br_desc {
        display: none;
    }

    .br_mob {
        display: block;
    }
}
</style>