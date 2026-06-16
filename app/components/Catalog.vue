<template>
    <nav class="catalog">
        <div class="catalog__container">
            <a href="/" class="catalog__logo-link" @click.prevent="emit('navigate', 'home')">
                <img src="../public/logo_placeholder.jpg" alt="Логотип Стандарт Экспресс" class="catalog__logo">
            </a>

            <ul class="catalog__list">
                <li class="catalog__item"><a href="#" class="catalog__link"
                        @click.prevent="emit('navigate', 'loaders')">Грузчики</a></li>
                <li class="catalog__item"><a href="#" class="catalog__link"
                        @click.prevent="emit('navigate', 'moves')">Переезды</a></li>
                <li class="catalog__item"><a href="#" class="catalog__link"
                        @click.prevent="emit('navigate', 'rigging')">Такелажные работы</a></li>
                <li class="catalog__item"><a href="#" class="catalog__link"
                        @click.prevent="emit('navigate', 'transportation')">Грузоперевозки</a></li>
                <li class="catalog__item"><a href="#" class="catalog__link"
                        @click.prevent="emit('navigate', 'handymen')">Разнорабочие</a></li>
                <li class="catalog__item"><a href="#" class="catalog__link"
                        @click.prevent="emit('navigate', 'legal')">Юридическим лицам</a></li>
            </ul>
        </div>
    </nav>
</template>

<script setup lang="ts">
const emit = defineEmits<{
    (e: 'navigate', route: string): void
}>();
</script>
<style scoped lang="scss">
.catalog {
    width: 100%;
    background-color: #FFFFFF;
}

.catalog__container {
    max-width: 1600px;
    height: 62px;
    margin: 5px auto;
    padding: 0 200px;

    display: flex;
    align-items: center;
    justify-content: flex-start;
    gap: 73px;
}

.catalog__logo {
    width: 146px;
    height: 35px;
    display: block;
}

.catalog__list {
    display: flex;
    list-style: none;
    margin: 0;
    padding: 0;
    gap: 55px;
    align-items: center;
    height: 100%;
}

.catalog__link {
    text-decoration: none;
    color: #000;
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 500;
    font-size: 16px;
    white-space: nowrap;
    transition: color 0.2s;

    &:hover {
        color: #ED9121;
    }
}

@media (max-width: 1600px) {
    .catalog__container {
        display: none;
    }
}
</style>