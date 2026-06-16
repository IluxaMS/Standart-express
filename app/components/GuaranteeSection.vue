<template>
    <section class="guarantee-section">
        <img src="../public/decor-truck-left.png" alt="" class="decor decor--truck-left" />
        <img src="../public/decor-black-bottom.png" alt="" class="decor decor--black-bottom" />
        <img src="../public/decor-orange-top.png" alt="" class="decor decor--orange-top" />
        <img src="../public/decor-loader-right.png" alt="" class="decor decor--loader-right" />
        <div class="guarantee-content">
            <h2 class="guarantee-title">
                По вашей заявке услуга «Грузчики» будет выполнена точно в срок и по цене, которую вы можете рассчитать
                на нашем сайте.
            </h2>
            <p class="guarantee-subtitle">
                Работаем круглосуточно! Выезжаем на объекты в Москве.
            </p>
        </div>
    </section>
</template>

<script setup lang="ts">
</script>

<style scoped lang="scss">
.guarantee-section {
    position: relative;
    width: 100%;
    min-height: 400px;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    padding: 60px 20px;
}

.guarantee-bg-img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: 1;
}

.guarantee-overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(255, 255, 255, 0.9);
    z-index: 2;
}

.guarantee-content {
    position: relative;
    z-index: 3;
    max-width: 800px;
    text-align: center;
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.guarantee-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 32px;
    line-height: 140%;
    text-transform: uppercase;
    color: #000;
    margin: 0;
    width: 86%;
    margin-left: 60px;
}

.guarantee-subtitle {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 300;
    font-size: 24px;
    line-height: 140%;
    color: #000;
    margin: 0;
}

.decor {
    position: absolute;
    z-index: 2;
    pointer-events: none;
}

.decor--truck-left {
    left: 0;
    top: 33%;
    transform: translateY(-50%);
    width: 359px;
    height: auto;
}

.decor--black-bottom {
    left: 16%;
    bottom: 0;
    width: 70px;
    height: auto;
}

.decor--orange-top {
    right: 20%;
    top: 0;
    width: 70px;
    height: auto;
}

.decor--loader-right {
    right: 0;
    bottom: 5%;
    width: 321px;
    height: auto;
}

@media (max-width: 768px) {
    .guarantee-section {
        padding: 0px 14px;
        min-height: 300px;
    }

    .guarantee-title {
        font-size: 20px;
        width: 106%;
        margin-left: -10px;
    }

    .guarantee-subtitle {
        font-size: 18px;
    }

    .decor {
        display: none;
    }

    .guarantee-content {
        margin-top: -30px;
    }
}
</style>