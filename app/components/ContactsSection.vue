<template>
    <section class="contacts-section">
        <img src="../public/decor_orange_top.png" alt="" class="decor decor--orange-top" />
        <img src="../public/decor_orange_worker.png" alt="" class="decor decor--worker" />
        <img src="../public/decor_black_bottom.png" alt="" class="decor decor--black-bottom" />

        <div class="contacts-container">
            <h2 class="contacts-title">Контакты</h2>

            <div class="contacts-layout">
                <div class="contacts-info">
                    <div class="info-block">
                        <h3 class="info-label">Адрес</h3>
                        <div class="info-row">
                            <img src="../public/icon_map_pin.png" alt="pin" class="info-icon pin-icon" />
                            <span class="info-text">127018, Россия, г. Москва, Сущевский вал 5 стр 19</span>
                        </div>
                    </div>

                    <div class="info-block">
                        <h3 class="info-label">Телефон</h3>
                        <div class="info-row">
                            <img src="../public/tel_icon3.png" alt="phone" class="info-icon phone-icon" />
                            <div class="phones-wrapper">
                                <a href="tel:88007005153" class="info-text link">8 (800) 700-51-53</a>
                                <span class="separator">,</span>
                                <a href="tel:+79652265790" class="info-text link">+7 (965) 226-57-90</a>
                            </div>
                        </div>
                        <p class="info-subtext">Принимаем звонки ежедневно<br />с 8:00 до 20:00 (по МСК)</p>
                    </div>

                    <div class="info-block">
                        <h3 class="info-label">Почта</h3>
                        <div class="info-row">
                            <img src="../public/mail_icon2.png" alt="mail" class="info-icon mail-icon" />
                            <a href="mailto:info@standart-express.ru"
                                class="info-text link">info@standart-express.ru</a>
                        </div>
                        <p class="info-subtext">Выполняем заказы: 24/7</p>
                    </div>

                    <div class="socials-row">
                        <a href="https://vk.com/standart_express" target="_blank" class="social-link"><img src="../public/icon_vk.png" alt="VK" /></a>
                        <a href="https://www.youtube.com/standart_express" target="_blank"  class="social-link"><img src="../public/icon_youtube.png" alt="YouTube" /></a>
                        <a href="https://www.whatsapp.com/standart_express" target="_blank"  class="social-link"><img src="../public/whatsapp.jpg" alt="WhatsApp" /></a>
                        <a href="https://t.me/standart_express" target="_blank" class="social-link"><img src="../public/telegram.jpg" alt="Telegram" /></a>
                    </div>
                </div>

                <div class="contacts-form-wrapper">
                    <form class="consultation-form" @submit.prevent="submitForm">
                        <h3 class="form-title">Заказать консультацию</h3>

                        <div class="input-group input-wrapper">
                            <input type="text" placeholder="Имя" v-model="formData.name" @input="validateName"
                                :class="{ 'input-error': errors.name }" class="form-input" required />
                            <span v-if="errors.name" class="error-text">Ошибка</span>
                        </div>

                        <div class="input-group input-wrapper">
                            <input type="tel" placeholder="Телефон" v-model="formData.phone" @input="validatePhone"
                                :class="{ 'input-error': errors.phone }" class="form-input" required />
                            <span v-if="errors.phone" class="error-text">Ошибка</span>
                        </div>

                        <button type="submit" class="submit-btn">Отправить</button>
                    </form>
                </div>
            </div>

            <div class="map-wrapper">
                <iframe
                    src="https://yandex.ru/map-widget/v1/?ll=37.593956%2C55.794522&z=17&l=map&pt=37.593956,55.794522,pm2rdm"
                    width="100%" height="100%" frameborder="0" allowfullscreen="true"
                    style="position:relative; border-radius: 20px;"></iframe>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { reactive } from 'vue';

const formData = reactive({
    name: '',
    phone: ''
});

const errors = reactive({
    name: false,
    phone: false
});

const validateName = () => {
    const regex = /^[a-zA-Zа-яА-Я\s]*$/;
    errors.name = !regex.test(formData.name) && formData.name.length > 0;
};

const validatePhone = () => {
    errors.phone = /[a-zA-Zа-яА-Я]/.test(formData.phone);
};

const submitForm = () => {
    if (errors.name || errors.phone) return;

    console.log('Форма отправлена:', formData);
    alert('Спасибо! Мы свяжемся с вами в ближайшее время.');
    formData.name = '';
    formData.phone = '';
    errors.name = false;
    errors.phone = false;
};
</script>

<style scoped lang="scss">
.contacts-section {
    position: relative;
    width: 100%;
    min-height: 1086px;
    background-color: #F5F5F5;
    padding: 60px 0;
    overflow: hidden;
}

.decor {
    position: absolute;
    z-index: 1;
    pointer-events: none;
}

.decor--orange-top {
    top: 0;
    left: 100px;
    width: 35px;
    height: auto;
}

.decor--worker {
    top: 285px;
    right: 0;
    width: 111px;
    height: auto;
}

.decor--black-bottom {
    bottom: 46%;
    left: 46%;
    width: 55px;
    height: auto;
}

.contacts-container {
    position: relative;
    z-index: 2;
    max-width: 1600px;
    margin: 0 auto;
    padding: 0 200px;
}

.contacts-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 50px;
    line-height: 100%;
    color: #000;
    margin: 0 0 50px 0;
}

.contacts-layout {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 50px;
}

.contacts-info {
    max-width: 500px;
    display: flex;
    flex-direction: column;
    gap: 30px;
}

.info-block {
    display: flex;
    flex-direction: column;
    gap: 15px;
}

.info-label {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 20px;
    line-height: 100%;
    color: #000;
    margin: 0;
}

.info-row {
    display: flex;
    align-items: center;
    gap: 13px;
}

.info-icon {
    width: 20px;
    height: 20px;
    object-fit: contain;
    flex-shrink: 0;
}

.phone-icon {
    width: 23px;
    height: 23px;
}

.phones-wrapper {
    display: flex;
    align-items: center;
    gap: 5px;
    flex-wrap: wrap;
}

.separator {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 300;
    font-size: 18px;
    color: #000;
    margin-right: 5px;
}

.info-text {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 300;
    font-size: 18px;
    line-height: 100%;
    color: #000;
    text-decoration: none;

    &.link {
        transition: color 0.2s;

        &:hover {
            color: #ED9121;
        }
    }
}

.info-subtext {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 300;
    font-size: 13px;
    line-height: 115%;
    color: #000;
    margin: -10px 0 0 35px;
    /* Отступ под иконку */
}

.socials-row {
    display: flex;
    gap: 15px;
}

.social-link {
    width: 32px;
    height: 32px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: transform 0.2s;

    img {
        width: 100%;
        height: 100%;
        object-fit: contain;
    }

    &:hover {
        transform: scale(1.1);
    }
}

.contacts-form-wrapper {
    width: 460px;
    background: #FFFFFF;
    border-radius: 30px;
    padding: 40px;
    margin-top: -25px;
}

.consultation-form {
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.form-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 24px;
    line-height: 100%;
    color: #000;
    margin: 0 0 10px 0;
    text-align: center;
}

.input-group {
    width: 100%;
}

.form-input {
    width: 100%;
    height: 60px;
    border: 1px solid #CECECE;
    border-radius: 29.5px;
    padding: 0 25px;
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 16px;
    color: #000;
    outline: none;
    box-sizing: border-box;
    transition: border-color 0.2s;

    &::placeholder {
        color: #999;
    }

    &:focus {
        border-color: #ED9121;
    }
}

.submit-btn {
    width: 100%;
    height: 60px;
    border-radius: 100px;
    background-color: #ED9121;
    color: #FFFFFF;
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 16px;
    border: none;
    cursor: pointer;
    transition: filter 0.2s;

    &:hover {
        filter: brightness(1.1);
    }

    &:active {
        transform: scale(0.98);
    }
}

.map-wrapper {
    width: 100%;
    max-width: 1208px;
    height: 467px;
    border-radius: 20px;
    overflow: hidden;
    margin: 0 auto;
    background-color: #E0E0E0;
}

.input-group.input-wrapper {
    position: relative;
}

.form-input.input-error {
    border-color: #FF0000;

    &:focus {
        border-color: #FF0000;
    }
}

.error-text {
    position: absolute;
    bottom: -20px;
    left: 25px;
    color: #FF0000;
    font-size: 12px;
    font-family: "Euclid Circular A", sans-serif;
    margin-bottom: 3px;
}

@media (max-width: 1300px) {
    .contacts-container {
        padding: 0 40px;
    }

    .contacts-layout {
        flex-direction: column;
        gap: 40px;
    }

    .contacts-info {
        max-width: 85%;
        margin-top: -10px;
        gap: 20px;
    }

    .contacts-form-wrapper {
        width: 100%;
        max-width: 500px;
    }

    .map-wrapper {
        height: 400px;
    }
}

@media (max-width: 768px) {
    .contacts-section {
        padding: 40px 0;
        min-height: auto;
    }

    .decor {
        display: none;
    }

    .contacts-container {
        padding: 0 20px;
        margin-top: -15px;
    }

    .contacts-title {
        font-size: 32px;
        margin-bottom: 30px;
    }

    .contacts-layout {
        gap: 30px;
    }

    .info-label {
        font-size: 18px;
    }

    .info-text {
        font-size: 16px;
        line-height: 125%;
    }

    .separator {
        margin-left: -5px;
    }

    .contacts-form-wrapper {
        padding: 30px 20px;
    }

    .form-title {
        font-size: 20px;
    }

    .map-wrapper {
        height: 466px;
        width: 343px;
    }

    .pin-icon {
        margin-bottom: 20px;
    }

    .form-input {
        width: 85%;
        margin-left: 7%;
    }

    .submit-btn {
        width: 85%;
        margin-left: 7%;
    }
}
</style>