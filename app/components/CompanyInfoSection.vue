<template>
    <section class="company-section">
        <div class="company-container">
            <img src="../public/decor_line_left.jpg" alt="" class="company-decor company-decor--left" />

            <div class="company-content">
                <h2 class="company-title">Компания «Стандарт Экспресс»</h2>
                <p class="company-text">
                    Работая с 2013 года мы стали признанными экспертами в области погрузочно-разгрузочных работ. Это
                    подтверждается рекомендательными и благодарственными письмами от крупных корпораций и<br
                        class="transfer"> сотнями
                    положительных отзывов от<br class="transfer"> клиентов.
                    <br>Помимо погрузочно-разгрузочных работ мы выполняем<br class="transfer_2"> такелажные работы до 50
                    тонн,
                    перевозим грузы по всей России от 1 кг, предоставляем спецтехнику, разнорабочих, аутсорсинг
                    персонала на склады и любые другие объекты.
                    <br>В базе компаний более 150 000 клиентов "Стандарт Экспресс": частные лица, крупные торговые и
                    производственные предприятия.
                </p>
            </div>

            <div class="company-image-wrapper">
                <img src="../public/company_team.png" alt="Команда Стандарт Экспресс" class="company-image" />
            </div>
        </div>
    </section>
</template>

<style scoped lang="scss">
.company-section {
    width: 100%;
    background-color: #ffffff;
    overflow: hidden;
    position: relative;
}

.company-container {
    max-width: 1627px;
    margin: 0 auto;
    position: relative;
    min-height: 425px;
    display: flex;
    align-items: center;
    padding-left: 200px;
    padding-right: 200px;
}

.company-content {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    z-index: 2;
    width: 44%;
    max-width: 517px;
}

.company-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 50px;
    line-height: 120%;
    color: #000;
    margin: 0;
    margin-bottom: 15px;
    width: 524px;
}

.company-text {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 300;
    font-size: 16px;
    line-height: 150%;
    color: #000;
    margin: 0;
    max-width: 534px;
    text-align: left;
}

.company-image-wrapper {
    position: absolute;
    right: 200px;
    top: 0;
    height: 100%;
    width: 610px;
    display: flex;
    align-items: center;
}

.company-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 20px;
}

.company-decor {
    position: absolute;
    z-index: 1;
    opacity: 1;
    pointer-events: none;
}

.company-decor--left {
    top: 45px;
    left: -30px;
    width: 180px;
}

.transfer {
    display: none;
}

@media (max-width: 1024px) {
    .company-section {
        background-color: #f5f5f5;
    }

    .company-container {
        padding: 40px 20px;
        flex-direction: column;
        height: auto;
        min-height: auto;
        align-items: stretch;
    }

    .company-content {
        width: 100%;
        max-width: 100%;
        margin-bottom: 30px;
        align-items: flex-start;
        text-align: left;
    }

    .company-title {
        font-size: 32px;
        line-height: 1.4;
        width: 100%;
        margin: 0;
        margin-bottom: 20px;
        color: #000;
    }

    .company-text {
        font-size: 16px;
        line-height: 150%;
        color: #000;
        max-width: 100%;
        margin-bottom: 0;
        letter-spacing: 0.7px;

        .transfer {
            display: block;
            content: "";
            margin-bottom: 16px;
        }
    }

    .company-image-wrapper {
        position: relative;
        right: auto;
        top: auto;
        width: 100%;
        height: auto;
        aspect-ratio: 343 / 220;
    }

    .company-image {
        border-radius: 12px;
        width: 100%;
        height: 100%;
    }

    .company-decor,
    .transfer_2 {
        display: none;
    }
}
</style>