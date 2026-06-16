<template>
    <section class="values-section">
        <img src="../public/decor_top_right.png" alt="" class="values-decor values-decor--top-right" />
        <img src="../public/decor_bottom_left.png" alt="" class="values-decor values-decor--bottom-left" />

        <div class="values-container">
            <h2 class="values-title">НАШИ ЦЕННОСТИ</h2>

            <div class="values-grid">
                <div class="value-item">
                    <div class="icon-wrapper">
                        <img src="../public/icon_responsibility.png" alt="Ответственность"
                            class="value-icon_responsibility" />
                    </div>
                    <p class="value-text">Ответственность</p>
                </div>

                <div class="value-item">
                    <div class="icon-wrapper">
                        <img src="../public/icon_honesty.png" alt="Честность" class="value-icon_honesty" />
                    </div>
                    <p class="value-text">Строить открытые<br>и честные отношения</p>
                </div>

                <div class="value-item">
                    <div class="icon-wrapper">
                        <img src="../public/icon_efficiency.png" alt="Эффективность" class="value-icon_efficiency" />
                    </div>
                    <p class="value-text">Делать больше<br>с меньшими<br class="transfer"> затратами</p>
                </div>

                <div class="value-item">
                    <div class="icon-wrapper">
                        <img src="../public/icon_development.png" alt="Развитие" class="value-icon_development" />
                    </div>
                    <p class="value-text">Учиться и развиваться</p>
                </div>

                <div class="value-item">
                    <div class="icon-wrapper">
                        <img src="../public/icon_team.png" alt="Команда" class="value-icon_team" />
                    </div>
                    <p class="value-text">Создавать<br>позитивную<br class="transfer"> команду</p>
                </div>

                <div class="value-item">
                    <div class="icon-wrapper">
                        <img src="../public/icon_empathy.png" alt="Чуткость" class="value-icon_empathy" />
                    </div>
                    <p class="value-text">Развивать чуткость</p>
                </div>

                <div class="value-item">
                    <div class="icon-wrapper">
                        <img src="../public/icon_serious.png" alt="Легкость" class="value-icon_serious" />
                    </div>
                    <p class="value-text">Не быть слишком<br>серьезным</p>
                </div>

                <div class="value-item">
                    <div class="icon-wrapper">
                        <img src="../public/icon_influence.png" alt="Влияние" class="value-icon_influence" />
                    </div>
                    <p class="value-text">Позитивно влиять<br>на дела клиентов</p>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped lang="scss">
.values-section {
    position: relative;
    width: 100%;
    height: 610px;
    background-color: #F5F5F5;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
}

.values-container {
    position: relative;
    z-index: 2;
    max-width: 1600px;
    width: 100%;
    margin: 0 auto;
    margin-bottom: 60px;
    padding: 0 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.values-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    color: #000;
    text-transform: uppercase;
    margin: 0 0 80px 0;
    letter-spacing: 0%;
    text-align: center;
}

.values-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 40px 30px;
    width: 100%;
    max-width: 1200px;
}

.value-item {
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

.value-icon_responsibility {
    width: 57px;
    height: 57px;
    object-fit: contain;
}

.value-icon_honesty {
    width: 64px;
    height: 64px;
    object-fit: contain;
}

.value-icon_efficiency {
    width: 50px;
    height: 50px;
    object-fit: contain;
}

.value-icon_development {
    width: 47px;
    height: 50px;
    object-fit: contain;
}

.value-icon_team {
    width: 56px;
    height: 56px;
    object-fit: contain;
}

.value-icon_empathy {
    width: 55px;
    height: 55px;
    object-fit: contain;
}

.value-icon_serious {
    width: 64px;
    height: 64px;
    object-fit: contain;
}

.value-icon_influence {
    width: 57px;
    height: 57px;
    object-fit: contain;
}

.value-text {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 140%;
    color: #000;
    margin: 0;
}

.values-decor {
    position: absolute;
    z-index: 1;
    pointer-events: none;
}

.values-decor--top-right {
    top: 0;
    right: 100px;
    width: 70px;
    height: auto;
}

.values-decor--bottom-left {
    bottom: 0;
    left: 100px;
    width: 70px;
    height: auto;
}

.transfer {
    display: none;
}

@media (max-width: 1024px) {
    .values-section {
        height: auto;
        min-height: 770px;
        padding: 0;
    }

    .values-container {
        padding: 50px 20px 0;
    }

    .values-title {
        font-size: 32px;
        margin-bottom: 40px;
    }

    .values-grid {
        grid-template-columns: repeat(2, 1fr);
        gap: 40px 20px;
        max-width: 400px;
    }

    .icon-wrapper {
        width: 70px;
        height: 70px;
        margin-bottom: 15px;
    }

    .value-icon {
        width: 35px;
        height: 35px;
    }

    .value-text {
        font-size: 14px;
        line-height: 130%;
    }

    .values-decor {
        display: none;
    }

    .transfer {
        display: block;
    }
}
</style>