<template>
    <header class="header">
        <div class="header__container">
            <div class="header__left">
                <div class="header__menu-trigger">
                    <img src="../public/burger_menu.jpg" alt="Иконка меню">
                    <span class="header__menu-text">Меню</span>
                </div>
                <nav class="header__nav">
                    <ul class="header__nav-list">
                        <li><a href="#" class="header__nav-link" @click.prevent="emit('navigate', 'company')">О
                                компании</a></li>
                        <li><a href="#" class="header__nav-link"
                                @click.prevent="emit('navigate', 'vacancies')">Вакансии</a></li>
                        <li><a href="#" class="header__nav-link" @click.prevent="emit('navigate', 'news')">Новости</a>
                        </li>
                        <li><a href="#" class="header__nav-link"
                                @click.prevent="emit('navigate', 'contacts')">Контакты</a></li>
                    </ul>
                </nav>
            </div>

            <img src="../public/logo_placeholder_black.jpg" alt="Logo" class="mobile-logo">

            <div class="header__right">
                <div class="header__contact-item">
                    <img src="../public/mail_icon.jpg" alt="Иконка mail">
                    <div class="header__contact-text">
                        <a href="mailto:info@standart-express.ru" class="header__email">info@standart-express.ru</a>
                        <span class="header__subtext">Выполняем заказы: 24/7</span>
                    </div>
                </div>
                <div class="header__contact-item header__contact-item_phone">
                    <img src="../public/tel_icon.jpg" alt="Иконка телефона">
                    <div class="header__phones">
                        <a href="tel:88007005153" class="header__phone-main">8 (800) 700-51-53</a>
                        <span class="header__city-mobile">Ваш город:<br>Санкт-Петербург</span>
                        <a href="tel:+79652265790" class="header__phone-sub">+7 (965) 226-57-90</a>
                    </div>
                </div>
                <div class="header__socials">
                    <a href="https://www.whatsapp.com/standart_express" target="_blank" class="header__social-whatsapp"
                        aria-label="WhatsApp">
                        <img src="../public/whatsapp.jpg" alt="WhatsApp">
                    </a>
                    <a href="https://t.me/standart_express" target="_blank" class="header__social-telegram"
                        aria-label="Telegram">
                        <img src="../public/telegram.jpg" alt="Telegram">
                    </a>
                </div>
                <Button label="Перезвоните мне" size="md" />
                <div class="header__geo">
                    <img class="header__geo-icon" src="../public/geo_icon.jpg" alt="Иконка гео">
                    <span class="header__city">Санкт -<br>Петербург</span>
                </div>
            </div>
        </div>
    </header>
</template>

<script setup lang="ts">
const emit = defineEmits<{
    (e: 'navigate', route: string): void
}>();
</script>

<style scoped lang="scss">
.header {
    width: 100%;
    background-color: #FFFFFF;
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 500;
}

.header__container {
    max-width: 1600px;
    margin: 0 auto;
    padding: 0 200px;
    height: 84px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.header__left {
    display: flex;
    align-items: center;
    gap: 48px;
}

.header__menu-trigger {
    display: flex;
    flex-direction: column;
    align-items: center;
    cursor: pointer;
}

.header__menu-text {
    font-size: 11px;
}

.header__nav-list {
    display: flex;
    list-style: none;
    gap: 24px;
    margin: 0;
    padding: 0;
}

.header__nav-link {
    text-decoration: none;
    color: rgba(0, 0, 0, 0.7);
    font-size: 14px;
    transition: color 0.2s;

    &:hover {
        color: #ED9121;
    }
}

.header__right {
    display: flex;
    align-items: center;
    gap: 20px;
}

.header__contact-item {
    display: flex;
    align-items: flex-start;
    gap: 10px;
}

.header__contact-item_phone {
    margin-left: 14px;
}

.header__contact-text {
    display: flex;
    flex-direction: column;
}

.header__email {
    font-size: 14px;
    font-weight: 300;
    text-decoration: none;
    color: #000;
    line-height: 1.4;
}

.header__subtext {
    font-size: 12px;
    font-weight: 300;
    color: #000;
}

.header__phones {
    display: flex;
    flex-direction: column;
}

.header__phone-main {
    font-size: 14px;
    font-weight: 300;
    text-decoration: none;
    color: #000;
    line-height: 1.4;
    padding-left: 10px;
}

.header__city-mobile {
    display: none;
}

.header__phone-sub {
    font-size: 14px;
    font-weight: 300;
    text-decoration: none;
    color: #000;
}

.header__socials {
    display: flex;
    gap: 12px;
    margin-left: 8px;
}

.header__social-whatsapp {
    &:active {
        transform: scale(0.96);
    }
}

.header__social-telegram {
    &:active {
        transform: scale(0.96);
    }
}

.header__geo {
    display: flex;
    align-items: center;
    gap: 6px;
    color: #000;
    margin-left: -4px;
    font-size: 14px;
    font-weight: 500;
    text-decoration: dashed underline;
    opacity: 70%;
    line-height: 1.2;

    .header__geo-icon {
        padding-bottom: 20px;
        width: 11px;
    }
}

.mobile-logo {
    display: none;
}

@media (max-width: 1400px) {
    .header__container {
        padding: 0 100px;
    }
}

@media (max-width: 1200px) {
    .header__container {
        padding: 0 50px;
    }

    .header__left {
        gap: 30px;
    }

    .header__nav-list {
        gap: 16px;
    }

    .header__right {
        gap: 15px;
    }
}

@media (max-width: 768px) {
    .header {
        background-color: #000;
        height: 69px;
    }

    .header__container {
        height: 100%;
        padding: 0 20px;
        justify-content: space-between;
        align-items: center;
        position: relative;
    }

    .header__nav,
    .header__contact-item:not(.header__contact-item_phone),
    .header__socials,
    .app-button,
    .header__geo {
        display: none;
    }

    .header__left {
        order: 1;
        gap: 0;
    }

    .header__menu-trigger {
        flex-direction: column;
        align-items: center;

        img {
            width: 32px;
            height: 32px;
            filter: invert(1);
        }

        .header__menu-text {
            color: #FFFFFF;
            font-size: 11px;
            font-weight: 500;
        }
    }

    .mobile-logo {
        display: block;
        order: 2;
        height: 36px;
        width: auto;
        position: relative;
        margin: 0 auto;
    }

    .header__right {
        order: 3;
        gap: 0;
        margin: 0;
    }

    .header__contact-item_phone {
        margin-left: 0;
        flex-direction: column;
        align-items: flex-end;
        justify-content: center;
        gap: 0;

        img {
            display: none;
        }
    }

    .header__phone-main {
        color: #FFFFFF;
        font-size: 14px;
        font-weight: 500;
        padding-left: 0;
        line-height: 1.2;
    }

    .header__phone-sub {
        display: none;
    }

    .header__subtext {
        color: #FFFFFF;
        font-size: 12px;
        opacity: 0.8;
        margin-top: 2px;
        display: block;
        line-height: 1.2;
    }

    .header__city-mobile {
        color: #FFFFFF;
        font-size: 12px;
        opacity: 0.8;
        margin-top: 4px;
        display: block;
        line-height: 1.2;
        text-align: left;
    }
}
</style>