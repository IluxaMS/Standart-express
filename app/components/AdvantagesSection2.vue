<template>
    <section class="advantages-section">
        <div class="advantages-container">
            <div class="advantages-list">
                <div class="advantage-item advantage-item_map">
                    <img src="../public/icon_map.png" alt="Скидка" class="advantage-icon" />
                    <p class="advantage-text">Работаем в 1047 городах России, охват<br /> более 100 000 населенных
                        пунктов</p>
                </div>
                <div class="advantage-item advantage-item_suitcase">
                    <img src="../public/icon_suitcase.png" alt="Время" class="advantage-icon" />
                    <p class="advantage-text">10+ лет на рынке</p>
                </div>
                <div class="advantage-item advantage-item_boxes">
                    <img src="../public/icon_boxes.png" alt="Клиенты" class="advantage-icon" />
                    <p class="advantage-text">7 000<br class="transfer_1" /> заказов<br /> выполняем ежемесячно</p>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts"></script>

<style scoped lang="scss">
.advantages-section {
    width: 100%;
    padding: 60px 0;
    background-color: #f5f5f5;
    box-sizing: border-box;
}

.advantages-container {
    max-width: 1600px;
    margin: 0 auto;
    padding: 0 200px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.advantages-list {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 30px;
    width: 100%;
    max-width: 1115px;
}

.advantage-item {
    display: flex;
    align-items: center;
    gap: 14px;
}

.advantage-item_suitcase,
.advantage-item_boxes {
    margin-right: 40px;
}

.advantage-icon {
    width: 60px;
    height: 60px;
    object-fit: contain;
}

.advantage-text {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 500;
    font-size: 14px;
    line-height: 1.2;
    color: #000;
    margin-top: 10px;
}

.transfer_1 {
    display: none;
}

@media (max-width: 1024px) {
    .advantages-section {
        background-color: #f5f5f5;
        padding: 0px 0;
        margin-bottom: 15px;
    }

    .advantages-container {
        padding: 0 16px;
        margin: 0;
        max-width: 100%;
    }

    .advantages-list {
        gap: 42px;
        justify-content: space-between;
        max-width: 100%;
    }

    .advantage-item {
        flex-direction: column;
        text-align: center;
        align-items: center;
        gap: 8px;
        flex: 1;
        min-width: 0;
        margin-right: 0;
    }

    .advantage-item_suitcase,
    .advantage-item_boxes {
        margin-right: 0;
    }

    .advantage-item_suitcase {
        margin-bottom: 60px;
    }

    .advantage-icon {
        width: 65px;
        height: 65px;
    }

    .advantage-text {
        font-size: 13px;
        font-weight: 400;
        line-height: 1.3;
        color: #000;
        margin-top: 0;
    }

    .advantage-item_map .advantage-text br:first-of-type {
        display: none;
    }

    .advantage-item_boxes .advantage-text br:not(.transfer_1) {
        display: none;
    }

    .advantage-item_boxes .transfer_1 {
        display: block !important;
    }
}

@media (max-width: 360px) {
    .advantages-list {
        flex-wrap: wrap;
        justify-content: center;
        gap: 20px;
    }

    .advantage-item {
        flex-basis: 40%;
    }
}
</style>