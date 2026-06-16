<template>
    <section class="guarantee-section">
        <div class="guarantee-container">
            <h2 class="guarantee-title">Сохранность<br class="br_mob"> груза - главная задача</h2>
            <p class="guarantee-subtitle">Гарантируем сохранность груза на всех этапах работ</p>

            <div class="guarantee-grid">
                <div class="guarantee-item">
                    <div class="icon-wrapper">
                        <img src="../public/icon_shield.png" alt="Щит" class="guarantee-icon" />
                    </div>
                    <p class="item-text">Соблюдаем технику безопасности</p>
                </div>

                <div class="guarantee-item">
                    <div class="icon-wrapper">
                        <img src="../public/icon_document.png" alt="Документ" class="guarantee-icon" />
                    </div>
                    <p class="item-text">Материальная ответственность прописана в договоре</p>
                </div>

                <div class="guarantee-item">
                    <div class="icon-wrapper">
                        <img src="../public/icon_container_crane.png" alt="Контейнер на крючке"
                            class="guarantee-icon" />
                    </div>
                    <p class="item-text">Используем современное специализированное оборудование</p>
                </div>

                <div class="guarantee-item">
                    <div class="icon-wrapper">
                        <img src="../public/icon_worker_insurance.png" alt="Строитель со страховкой"
                            class="guarantee-icon" />
                    </div>
                    <p class="item-text">Сотрудничаем со<br class="br_mob"> страховыми компаниями</p>
                </div>

            </div>
        </div>
    </section>
</template>
>

<style scoped lang="scss">
.guarantee-section {
    width: 100%;
    min-height: 453px;
    background-color: #F5F5F5;
    padding: 60px 0;
    display: flex;
    justify-content: center;
}

.guarantee-container {
    max-width: 1600px;
    width: 100%;
    margin: 0 auto;
    padding: 0 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
}

.guarantee-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    color: #000;
    text-transform: uppercase;
    margin: 0 0 15px 0;
    max-width: 890px;
    letter-spacing: 0%;
}

.guarantee-subtitle {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 100%;
    color: #000;
    margin: 0 0 50px 0;
    max-width: 425px;
    letter-spacing: 0%;
}

.guarantee-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 40px;
    width: 100%;
    max-width: 1200px;
}

.guarantee-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
}

.icon-wrapper {
    width: 80px;
    height: 80px;
    background-color: #FFFFFF;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 20px;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
}

.guarantee-icon {
    object-fit: contain;
    display: block;
}

.guarantee-item:nth-child(1) .guarantee-icon {
    width: 50px;
    height: 50px;
}

.guarantee-item:nth-child(2) .guarantee-icon {
    width: 46px;
    height: 46px;
}

.guarantee-item:nth-child(3) .guarantee-icon {
    width: 54px;
    height: 54px;
}

.guarantee-item:nth-child(4) .guarantee-icon {
    width: 60px;
    height: 60px;
}

.item-text {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 140%;
    color: #000;
    margin: 0;
    letter-spacing: 0%;
}

.br_mob {
    display: none;
}

@media (max-width: 1024px) {
    .guarantee-section {
        padding: 40px 0;
        min-height: auto;
    }

    .guarantee-title {
        font-size: 32px;
        max-width: 100%;
    }

    .guarantee-grid {
        grid-template-columns: 1fr;
        gap: 40px;
        max-width: 400px;
    }

    .guarantee-subtitle {
        margin-bottom: 40px;
    }

    .br_mob {
        display: block;
    }

    .item-text {
        width: 77%;
    }
}
</style>