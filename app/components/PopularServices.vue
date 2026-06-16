<template>
    <section class="popular-services">
        <div class="services-container">
            <h2 class="services-title">ПОПУЛЯРНЫЕ УСЛУГИ С ЦЕНАМИ</h2>

            <div class="services-list">
                <div v-for="(service, index) in visibleServices" :key="index" class="service-row">
                    <div class="service-name">{{ service.name }}</div>

                    <div class="service-action">
                        <span class="service-price">от {{ service.price }}₽</span>
                        <Button :label="service.buttonLabel" size="sm" outline class="order-btn" />
                    </div>
                </div>
            </div>

            <div class="services-footer">
                <button class="toggle-btn" @click="toggleShowAll">
                    {{ showAll ? 'Скрыть' : 'Показать все' }}
                </button>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

const initialServices = [
    { name: 'Услуги грузчиков для юридических лиц', price: 149, buttonLabel: 'Заказать' },
    { name: 'Услуги грузчиков для гос. структур', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики на производство', price: 149, buttonLabel: 'Заказать' },
    { name: 'Погрузка/разгрузка грузовых машин', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики на ночные работы', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики с НДС', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики без НДС', price: 149, buttonLabel: 'Заказать' },
];

const hiddenServices = [
    { name: 'Грузчики на срочные работы', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики по безналу', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики на такелажные работы', price: 149, buttonLabel: 'Заказать' },
    { name: 'Выгрузка (разгрузка) контейнера', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики на разовые работы', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики на подъем/спуск по этажам', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики для офисного переезда', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики на склад', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики для квартирного переезда', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики для вывоз мусора', price: 149, buttonLabel: 'Заказать' },
    { name: 'Перевозка мебели с грузчиками', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики с рохлей', price: 149, buttonLabel: 'Заказать' },
    { name: 'Грузчики-экспедиторы', price: 149, buttonLabel: 'Заказать' },
];

const showAll = ref(false);

const visibleServices = computed(() => {
    return showAll.value ? [...initialServices, ...hiddenServices] : initialServices;
});

const toggleShowAll = () => {
    showAll.value = !showAll.value;
};
</script>

<style scoped lang="scss">
.popular-services {
    width: 100%;
    padding: 80px 0;
    background-color: #FFFFFF;
}

.services-container {
    max-width: 1600px;
    margin: 0 auto;
    padding: 0 200px;
}

.services-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 32px;
    text-align: center;
    margin-bottom: 40px;
    color: #000;
    text-transform: uppercase;
}

.services-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.service-row {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 30px;
    border-radius: 50px;
    border: 1px solid transparent;
    transition: all 0.3s ease;
    cursor: pointer;

    &:hover {
        border-color: #ED9121;
        background-color: rgba(237, 145, 33, 0.03);

        .service-name {
            color: #ED9121;
            text-decoration: underline dashed 1px;
            text-underline-offset: 6px;
        }

        .order-btn {
            background-color: #ED9121 !important;
            color: #FFFFFF !important;
            border-color: #ED9121 !important;
        }
    }
}

.service-name {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 500;
    font-size: 18px;
    color: #000;
    transition: color 0.3s ease;
}

.service-action {
    display: flex;
    align-items: center;
    gap: 30px;
}

.service-price {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 20px;
    color: #000;
    white-space: nowrap;
}

.services-footer {
    margin-top: 40px;
    display: flex;
    justify-content: center;
}

.toggle-btn {
    min-width: 127px;
    height: 50px;
    border-radius: 100px;
    border: 1px solid #ED9121;
    background-color: #FFFFFF;
    color: #ED9121;
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 14px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease;
    padding: 0 20px;

    &:hover {
        background-color: #ED9121;
        color: #FFFFFF;
    }
}

@media (max-width: 1200px) {
    .services-container {
        padding: 0 20px;
    }

    .services-title {
        font-size: 26px;
        margin-bottom: 25px;
        text-align: center;
        width: 87%;
        margin-left: 10px;
    }

    .service-row {
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        gap: 15px;
        padding: 16px 2px;
        border-radius: 16px;
        flex-wrap: nowrap;
    }

    .service-name {
        font-size: 14px;
        line-height: 1.3;
        padding-right: 0;
        text-decoration: underline 1px !important;
        text-underline-offset: 5.5px;
        flex: 1;
        max-width: 131px;

        &:hover {
            color: #ED9121;
            text-decoration: underline 1px !important;
            text-underline-offset: 2px;
        }
    }

    .service-action {
        width: auto;
        margin-top: 0;
        justify-content: flex-end;
        gap: 12px;
        flex-shrink: 0;
    }

    .service-price {
        font-size: 16px;
    }

    .order-btn {
        padding: 8px 16px !important;
        font-size: 13px !important;
    }

    .toggle-btn {
        width: 100%;
        max-width: 385px;
        height: 48px;
    }

    .popular-services {
        padding: 30px 0;
    }
}
</style>