<template>
    <section class="mission-section">
        <img src="../public/mission_bg_1.png" alt="" class="mission-bg mission-bg--1" />
        <img src="../public/mission_bg_2.png" alt="" class="mission-bg mission-bg--2" />
        <img src="../public/decor_left_worker.png" alt="" class="mission-decor mission-decor--left" />
        <img src="../public/decor_right_top.png" alt="" class="mission-decor mission-decor--right" />

        <div class="mission-container">
            <div class="mission-content">
                <h2 class="mission-title">МИССИЯ КОМПАНИИ</h2>
                <p class="mission-text">
                    Предоставлять лучший сервис ручной и транспортной обработки грузов в России
                </p>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
</script>

<style scoped lang="scss">
.mission-section {
    position: relative;
    width: 100%;
    height: 268px;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
}

.mission-bg {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.mission-bg--1 {
    z-index: 1;
}

.mission-bg--2 {
    z-index: 2;
}

.mission-section::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.6);
    z-index: 1;
}

.mission-container {
    position: relative;
    z-index: 4;
    max-width: 1600px;
    width: 90%;
    margin: 0 auto;
    padding: 0 20px;
    display: flex;
    justify-content: center;
    margin-bottom: 30px;
}

.mission-content {
    text-align: center;
    max-width: 900px;
}

.mission-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    color: #FFFFFF;
    text-transform: uppercase;
    margin: 0 0 20px 0;
    letter-spacing: 0%;
}

.mission-text {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 20px;
    line-height: 160%;
    color: #FFFFFF;
    letter-spacing: 0%;
}

.mission-decor {
    position: absolute;
    z-index: 4;
    pointer-events: none;
}

.mission-decor--left {
    top: 150px;
    left: -26px;
    width: 280px;
    height: 83px;
    object-fit: contain;
}

.mission-decor--right {
    top: -12px;
    right: 124px;
    width: 76px;
    height: 208px;
    object-fit: contain;
}

@media (max-width: 1024px) {
    .mission-section {
        height: auto;
        min-height: 327px;
        padding: 60px 20px;
        align-items: flex-end;
    }

    .mission-bg--1,
    .mission-bg--2 {
        display: none;
    }

    .mission-section::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-image: url('../public/mission_bg_mobile.png');
        background-size: cover;
        background-position: center;
        z-index: 1;
    }

    .mission-section::after {
        background-color: rgba(0, 0, 0, 0.6);
        z-index: 2;
    }

    .mission-container {
        justify-content: center;
        padding: 0;
        z-index: 4;
    }

    .mission-content {
        text-align: center;
        max-width: 90%;
    }

    .mission-title {
        font-size: 26px;
        margin-bottom: 15px;
    }

    .mission-decor {
        display: none;
    }
}
</style>