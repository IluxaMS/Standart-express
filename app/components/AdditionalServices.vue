<template>
    <section class="additional-services-section">
        <img src="../public/reviews_decor_left2.png" alt="" class="decor-line-left">
        <img src="../public/reviews_decor_right.png" alt="" class="decor-line-right">

        <div class="services-container">
            <h2 class="services-title">ДОПОЛНИТЕЛЬНЫЕ УСЛУГИ В МОСКВЕ</h2>

            <div class="tags-wrapper">

                <a href="#" class="service-tag" style="width: 314px;">Грузчики для офисного переезда</a>
                <a href="#" class="service-tag" style="width: 328px;">Квартирный переезд с грузчиками</a>
                <a href="#" class="service-tag" style="width: 309px;">Перевозка мебели с грузчиками</a>

                <a href="#" class="service-tag" style="width: 261px;">Грузчики на производство</a>
                <a href="#" class="service-tag" style="width: 274px;">Переезд дома с грузчиками</a>
                <a href="#" class="service-tag" style="width: 278px;">Грузчики для вывоза мусора</a>
                <a href="#" class="service-tag" style="width: 356px;">Грузчики в Москве на разовые работы</a>

                <a href="#" class="service-tag" style="width: 324px;">Погрузочно-разгрузочные работы</a>
                <a href="#" class="service-tag" style="width: 284px;">Нанять грузчиков на такелаж</a>
                <a href="#" class="service-tag" style="width: 214px;">Грузчики с машиной</a>
                <a href="#" class="service-tag" style="width: 180px;">Демонтаж дома</a>

                <a href="#" class="service-tag" style="width: 265px;">Услуги грузчиков в Москве</a>
                <a href="#" class="service-tag" style="width: 200px;">Грузчики в Москве</a>
                <a href="#" class="service-tag" style="width: 185px;">Дачный переезд</a>
                <a href="#" class="service-tag" style="width: 329px;">Подъем на этаж в домах без лифта</a>

                <a href="#" class="service-tag" style="width: 211px;">Перевозка пианино</a>
            </div>
        </div>
    </section>
</template>

<style scoped lang="scss">
.additional-services-section {
    position: relative;
    width: 100%;
    min-height: 555px;
    background-color: #F5F5F5;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    font-family: "Euclid Circular A", sans-serif;
    padding: 60px 0;
}

.decor-line-left {
    position: absolute;
    top: 16%;
    left: 46px;
    transform: translateY(-50%);
    width: 73px;
    height: 185px;
    pointer-events: none;
    z-index: 1;
}

.decor-line-right {
    position: absolute;
    top: 68%;
    right: 46px;
    transform: translateY(-50%);
    width: 73px;
    height: 185px;
    pointer-events: none;
    z-index: 1;
    transform: rotateX(180deg);
}

.services-container {
    width: 1215px;
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    z-index: 2;
}

.services-title {
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    text-transform: uppercase;
    color: #000000;
    margin: 0 0 40px 0;
    text-align: center;
}

.tags-wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 15px;
    max-width: 1215px;
}

.service-tag {
    height: 62px;
    border-radius: 100px;
    background-color: #FFFFFF;
    border: 1px solid #E0E0E0;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 21px 27px;
    box-sizing: border-box;
    font-weight: 400;
    font-size: 16px;
    line-height: 100%;
    color: #000000;
    text-decoration: none;
    white-space: nowrap;
    transition: all 0.3s ease;

    &:hover {
        border-color: #ED9121;
        color: #ED9121;
        box-shadow: 0 4px 15px rgba(237, 145, 33, 0.1);
    }
}

@media (max-width: 1250px) {
    .services-container {
        width: 100%;
        padding: 0 20px;
    }

    .tags-wrapper {
        max-width: 100%;
    }

    .decor-line-left,
    .decor-line-right {
        display: none;
    }
}

@media (max-width: 768px) {
    .services-title {
        font-size: 26px;
        margin-bottom: 30px;
        line-height: 33px;
        font-weight: 700;
    }

    .service-tag {
        width: auto !important;
        flex-grow: 1;
        max-width: 100%;
        font-size: 14px;
        padding: 15px 20px;
        height: 50px;
    }
}
</style>