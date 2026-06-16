<template>
    <section class="advantages-section">
        <div class="advantages-container">
            <div class="advantages-list">
                <div class="advantage-item">
                    <img src="../public/icon_discount.png" alt="Скидка" class="advantage-icon" />
                    <p class="advantage-text">Скидка 10% на<br />первый заказ</p>
                </div>
                <div class="advantage-item">
                    <img src="../public/icon_time.png" alt="Время" class="advantage-icon" />
                    <p class="advantage-text">Будем у вас<br />через 60 минут</p>
                </div>
                <div class="advantage-item">
                    <img src="../public/icon_clients.png" alt="Клиенты" class="advantage-icon" />
                    <p class="advantage-text">Более 300<br />постоянных клиентов</p>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts"></script>

<style scoped lang="scss">
.advantages-section {
    width: 100%;
    padding: 40px 0;
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
    gap: 60px;
    width: 100%;
    max-width: 1000px;
}

.advantage-item {
    display: flex;
    align-items: center;
    gap: 20px;
}

.advantage-icon {
    width: 60px;
    height: 60px;
    object-fit: contain;
}

.advantage-text {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 300;
    font-size: 18px;
    line-height: 1.2;
    color: #000;
    margin: 0;
}

@media (max-width: 1024px) {
    .advantages-section {
        background-color: transparent;
        padding: 0;
    }

    .advantages-container {
        padding: 0;
        margin: 0;
        max-width: 100%;
    }

    .advantages-list {
        gap: 20px;
        justify-content: space-between;
    }

    .advantage-item {
        flex-direction: column;
        text-align: center;
        gap: 10px;
        flex: 1;
        min-width: 80px;
    }

    // Меняем путь к иконкам на белые версии
    .advantage-icon {
        width: 40px;
        height: 40px;

        &[alt="Скидка"] {
            content: url('../public/icon_discount_white.png');
        }

        &[alt="Время"] {
            content: url('../public/icon_time_white.png');
        }

        &[alt="Клиенты"] {
            content: url('../public/icon_clients_white.png');
        }
    }

    .advantage-text {
        font-size: 12px;
        line-height: 1.3;
        color: #ffffff;
    }
}

@media (max-width: 360px) {
    .advantages-list {
        flex-wrap: wrap;
        justify-content: center;
    }

    .advantage-item {
        flex-basis: 40%;
    }
}
</style>