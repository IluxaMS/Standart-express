<template>
    <section class="advantages-section">
        <div class="advantages-container">
            <div class="advantages-list">
                <div class="advantage-item advantage-item_map">
                    <img src="../public/icon_weight_black.png" alt="Переносим грузы"
                        class="advantage-icon advantage-icon_cargo" />
                    <p class="advantage-text">Переносим грузы от<br /> 100 кг до 50 тонн</p>
                </div>
                <div class="advantage-item advantage-item_suitcase">
                    <img src="../public/gear.png" alt="Спецоборудование"
                        class="advantage-icon advantage-icon_special-equipment_1" />
                    <p class="advantage-text">Используем специальное<br /> оборудование</p>
                </div>
                <div class="advantage-item advantage-item_boxes">
                    <img src="../public/hook.png" alt="Спецтехника"
                        class="advantage-icon advantage-icon_special-equipment_2" />
                    <p class="advantage-text">Предоставляем<br /> спецтехнику</p>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts"></script>

<style scoped lang="scss">
.advantages-section {
    width: 100%;
    padding-top: 80px;
    padding-bottom: 40px;
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
    max-width: 980px;
}

.advantage-item {
    display: flex;
    align-items: center;
    gap: 14px;
}

.advantage-item_boxes,
.advantage-item_suitcase {
    margin-right: -22px;
}

.advantage-icon {
    width: 60px;
    height: 60px;
    object-fit: contain;
}

.advantage-icon_cargo {
    width: 48px;
    height: 48px;
    margin-top: 10px;
}

.advantage-icon_special-equipment_1 {
    width: 50px;
    height: 50px;
}

.advantage-icon_special-equipment_2 {
    width: 62px;
    height: 62px;
}

.advantage-text {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 20px;
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