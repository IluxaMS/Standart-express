<template>
    <section class="services-text-section">
        <img src="../public/decor-left-orange.png" alt="" class="decor-left-orange" />
        <img src="../public/decor-right-truck.png" alt="" class="decor-right-truck" />

        <div class="content-container">
            <h2 class="section-title">Что такое такелаж?</h2>

            <div class="text-block">
                <div class="text-wrapper" :class="{ 'is-open': isBlock1Open }">
                    <div class="text-inner">

                        <div class="desktop-content">
                            <p class="main-text">
                                Такелажные снасти – это тросы, веревки, канаты и цепи, с помощью которых удерживают
                                рангоут и паруса парусного судна, а также управляют ими. Для изменения направления
                                тягового усилия и его увеличения используются шкивные конструкции: тали, блоки,
                                полиспасты, лебедки. Все это объединяется в единую систему, называемую такелажем,
                                которая очень эффективна для поднятия и перемещения груза, вследствие чего применяется
                                не только на море, но и на суше.<br class="desc">
                                Такелажные работы в Москве– самый экономичный и эффективный способ подъема, спуска, а
                                также перемещения на высоте крупногабаритных и тяжелых предметов которые не получается
                                передвигать вручную:
                                Носить все это вручную крайне трудно, если вообще возможно, особенно, когда речь идет о
                                спуске и поднятии вещей лифтом или по лестничным проемам. Габаритные предметы могут
                                просто не пройти в проемы или лестничные пролеты, поэтому их приходится доставлять через
                                окно, и подобные операции не обходятся без такелажных услуг.<br class="desc">
                                Перевозка груза логистическими организациями, переезды промышленных предприятий, офисов
                                и даже квартирные переезды – обычная сфера ответственности такелажников.<br
                                    class="desc">
                                Особенности проведения такелажа<br class="desc">
                                Такелажные работы требуют выполнения серьезных подготовительных мероприятий. Шкивные
                                конструкции должны закрепляться на той высоте, на которую происходит доставка груза, или
                                с которой его предстоит спускать.<br class="desc">
                                Использовать подъемный кран получается не всегда: он имеет ограничение по высоте. А это
                                значит, что мастер-такелажник должен располагать навыками промышленного альпинизма и
                                системой канатного доступа со страховкой, чем не обладают обычные грузчики. Также
                                требуется знание физики блоков, чтобы правильно рассчитать и смонтировать такелажные
                                устройства.<br class="desc">
                                Проведению работ предшествует инструктаж по технике безопасности и подготовка плана
                                спасательных мероприятий на случай нештатных ситуаций. Уровень организации и
                                материально-технического обеспечения должен быть очень велик, что отличает такелажные
                                услуги от услуг обычных грузчиков, хотя последние, как правило, работают в одной команде
                                со специалистом такелажником и машинистом подъемного крана (если он необходим).
                            </p>

                            <div class="hidden-content">
                                <p>Мы понимаем, что цена ошибки при работе с тяжелым оборудованием слишком высока.
                                    Поэтому каждый наш сотрудник проходит регулярную аттестацию и имеет допуски к
                                    работам на высоте и с грузоподъемными механизмами. Перед началом операции мы
                                    обязательно проводим осмотр места проведения работ, оцениваем несущую
                                    способность конструкций и разрабатываем оптимальную схему перемещения.</p>
                                <p>Выбирая нашу компанию для выполнения такелажных работ, вы получаете не просто
                                    бригаду рабочих, а команду инженеров-такелажников, которые гарантируют
                                    сохранность вашего имущества и безопасность окружающих. Мы работаем строго по
                                    договору, предоставляем все необходимые документы и несем полную материальную
                                    ответственность за результат.</p>
                            </div>
                        </div>

                        <div class="mobile-content">
                            <p class="mobile-text">
                                Такелажные снасти – это тросы, веревки, канаты и цепи, с помощью которых удерживают
                                рангоут и паруса парусного судна, а также управляют ими. Для изменения направления
                                тягового усилия и его увеличения используются шкивные конструкции: тали, блоки,
                                полиспасты, лебедки. Все это объединяется в единую систему, называемую такелажем,
                                которая очень эффективна для поднятия и перемещения груза, вследствие чего применяется
                                не только на море, но и на суше.
                                Такелажные работы в Москве– самый экономичный и эффективный способ подъема, спуска, а
                                также перемещения на высоте крупногабаритных и тяжелых предметов которые не получается
                                передвигать вручную:
                                Носить все это вручную крайне трудно, если вообще возможно, особенно, когда речь идет о
                                спуске и поднятии вещей лифтом или по лестничным проемам. Габаритные предметы могут
                                просто не пройти в проемы или лестничные пролеты, поэтому их приходится доставлять через
                                окно, и подобные операции не обходятся без такелажных услуг.
                                Перевозка груза логистическими организациями, переезды промышленных предприятий, офисов
                                и даже квартирные переезды – обычная сфера ответственности такелажников.
                                Особенности проведения такелажа
                                Такелажные работы требуют выполнения серьезных подготовительных мероприятий. Шкивные
                                конструкции должны закрепляться на той высоте, на которую происходит доставка груза, или
                                с которой его предстоит спускать.
                                Использовать подъемный кран получается не всегда: он имеет ограничение по высоте. А это
                                значит, что мастер-такелажник должен располагать навыками промышленного альпинизма и
                                системой канатного доступа со страховкой, чем не обладают обычные грузчики. Также
                                требуется знание физики блоков, чтобы правильно рассчитать и смонтировать такелажные
                                устройства.
                                Проведению работ предшествует инструктаж по технике безопасности и подготовка плана
                                спасательных мероприятий на случай нештатных ситуаций. Уровень организации и
                                материально-технического обеспечения должен быть очень велик, что отличает такелажные
                                услуги от услуг обычных грузчиков, хотя последние, как правило, работают в одной команде
                                со специалистом такелажником и машинистом подъемного крана (если он необходим).
                            </p>
                        </div>

                    </div>

                    <div class="fade-overlay"></div>
                </div>

                <button class="toggle-btn" @click="isBlock1Open = !isBlock1Open">
                    <img src="../public/arrow_down.png" alt="toggle" class="toggle-icon desktop-icon"
                        :class="{ 'rotated': isBlock1Open }" />
                    <span class="mobile-btn-text">{{ isBlock1Open ? 'Скрыть' : 'Показать все' }}</span>
                </button>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const isBlock1Open = ref(false);
const isBlock2Open = ref(false);
</script>

<style scoped lang="scss">
ul li {
    list-style: block;
}

.services-text-section {
    position: relative;
    width: 100%;
    min-height: 765px;
    background-color: #F5F5F5;
    padding: 110px 0;
    padding-bottom: 20px;
    overflow: hidden;
    font-family: "Euclid Circular A", sans-serif;
}

.decor-left-orange {
    position: absolute;
    left: 0%;
    top: 390px;
    width: 156px;
    height: 61px;
    pointer-events: none;
    z-index: 1;
}

.decor-right-truck {
    position: absolute;
    right: 0;
    top: 715px;
    width: 159px;
    height: 53px;
    pointer-events: none;
    z-index: 1;
}

.content-container {
    position: relative;
    z-index: 2;
    max-width: 1600px;
    margin: 0 auto;
    padding: 0 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.section-title {
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    text-transform: uppercase;
    color: #000000;
    margin: 0 0 40px 0;
    text-align: center;
    width: 668px;
}

.text-block {
    width: 100%;
    max-width: 1204px;
    margin-bottom: 20px;

    &.cities-block {
        margin-top: 10px;
    }
}

.text-wrapper {
    display: block;
    max-height: 416px;
    overflow: hidden;
    transition: max-height 0.6s cubic-bezier(0.25, 1, 0.5, 1);
    position: relative;

    &.is-open {
        max-height: 5000px;
    }
}

.cities-wrapper {
    max-height: 135px;

    &.is-open {
        max-height: 5000px;
    }
}

.text-inner {
    padding-bottom: 10px;
}

.hidden-content {
    opacity: 0;
    transform: translateY(-10px);
    transition: opacity 0.5s ease 0.1s, transform 0.5s ease 0.1s;

    .is-open & {
        opacity: 1;
        transform: translateY(0);
    }
}

.main-text,
.cities-text,
.cities-continuation,
p,
ul,
li {
    font-weight: 400;
    font-size: 16px;
    line-height: 160%;
    color: #333333;
    margin: 0 0 15px 0;
}

.cities-text,
.cities-continuation {
    font-weight: 300;
    font-size: 14px;
    margin-bottom: 0px;
}

ul {
    padding-left: 20px;
    list-style-type: disc;
}

h3 {
    font-weight: 700;
    font-size: 20px;
    margin: 30px 0 15px 0;
    color: #000;
}

.price-table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 15px;

    tr {
        border-bottom: 1px solid #E0E0E0;
    }

    td {
        padding: 12px 0;
        font-size: 15px;
        color: #333;

        &:last-child {
            text-align: right;
            font-weight: 600;
            white-space: nowrap;
        }
    }
}

.toggle-btn {
    display: block;
    margin: 6px auto 0;
    background: none;
    border: none;
    cursor: pointer;
    padding: 10px;
    position: relative;
    z-index: 5;
}

.toggle-icon {
    width: 33px;
    height: 33px;
    object-fit: contain;
    transition: transform 0.4s ease;

    &.rotated {
        transform: rotate(180deg);
    }
}

.mobile-content,
.mobile-btn-text,
.fade-overlay {
    display: none;
}

.main-text ul {
    list-style: none;
    padding-left: 20px;
    margin: 0 0 15px 0;
}

.main-text li {
    position: relative;
    padding-left: 15px;
    margin-bottom: 8px;

    &::before {
        content: '';
        position: absolute;
        left: 0;
        top: 9px;
        width: 4px;
        height: 4px;
        background-color: #333333;
        border-radius: 50%;
    }
}

@media (max-width: 1200px) {
    .section-title {
        width: 100%;
        font-size: 32px;
    }

    .text-block {
        max-width: 100%;
    }

    .decor-left-orange,
    .decor-right-truck {
        display: none;
    }
}

@media (max-width: 768px) {
    .services-text-section {
        min-height: 450px;
        padding: 0;
    }

    .content-container {
        padding: 0 20px;
    }

    .section-title {
        font-size: 26px;
        margin-bottom: 30px;
        line-height: 33px;
    }

    .desktop-content {
        display: none;
    }

    .mobile-content,
    .mobile-btn-text,
    .fade-overlay {
        display: block;
    }

    .mobile-text {
        font-size: 14px;
        line-height: 150%;
        color: #333;
    }

    .text-wrapper {
        max-height: 280px;
    }

    .cities-wrapper {
        max-height: 220px;
    }

    .fade-overlay {
        display: block;
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 100px;
        background: linear-gradient(to bottom, rgba(245, 245, 245, 0) 0%, rgba(245, 245, 245, 1) 100%);
        pointer-events: none;
        z-index: 3;
        transition: opacity 0.3s ease;

        .is-open & {
            opacity: 0;
        }
    }

    .toggle-btn {
        width: 100%;
        max-width: 343px;
        height: 50px;
        border: 1px solid #ED9121;
        border-radius: 100px;
        background-color: #FFFFFF;
        color: #ED9121;
        font-family: "Euclid Circular A", sans-serif;
        font-weight: 600;
        font-size: 16px;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-top: 20px;

        .desktop-icon {
            display: none;
        }

        .mobile-btn-text {
            display: inline-block;
        }

        &:active {
            background-color: #ED9121;
            color: #FFFFFF;
        }
    }

    .toggle-btn_2 {
        display: none;
    }

    .desc {
        display: none;
    }
}
</style>