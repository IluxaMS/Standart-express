<template>
    <section class="callback-section">
        <img src="../public/reviews_decor_right.png" alt="" class="decor-line-top">
        <img src="../public/decor-loader-bottom.png" alt="" class="decor-loader-bottom">

        <div class="callback-container">
            <div class="callback-content">
                <h2 class="callback-title">У ВАС ЕСТЬ<br> ВОПРОСЫ?</h2>
                <p class="callback-subtitle">Оставьте телефон и мы вам перезвоним</p>

                <form class="callback-form" @submit.prevent="submitForm">
                    <div class="input-wrapper">
                        <input type="tel" placeholder="+7" v-model="phone" @input="validatePhone"
                            :class="{ 'input-error': phoneError }" class="callback-input">
                        <span v-if="phoneError" class="error-text">Ошибка</span>
                    </div>

                    <button type="submit" class="callback-btn" :disabled="phoneError || phone.length < 10">
                        <img src="../public/tel_icon2.png" alt="Иконка телефона" class="tel_icon">
                        Перезвоните мне
                    </button>
                </form>

                <p class="callback-policy">
                    Отправляя заявку, вы соглашаетесь с <a href="/public/policy.txt" target="_blank"
                        class="policy-link">политикой обработки персональных данных</a>
                </p>
            </div>

            <div class="callback-image-block">
                <img src="../public/callback_image.png" alt="Грузчик с коробками" class="callback-img">
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const phone = ref('+7');
const phoneError = ref(false);

const validatePhone = () => {
    if (!phone.value.startsWith('+7')) {
        phone.value = '+7' + phone.value.replace(/^\+?7?/, '');
    }

    phoneError.value = /[a-zA-Zа-яА-Я]/.test(phone.value);
};

const submitForm = () => {
    if (!phoneError.value && phone.value.length >= 10) {
        console.log('Форма отправлена:', phone.value);
        alert('Заявка отправлена! Мы перезвоним вам.');
    }
};
</script>

<style scoped lang="scss">
.callback-section {
    position: relative;
    width: 100%;
    background-color: #FFFFFF;
    padding: 60px 0;
    overflow: hidden;
    font-family: "Euclid Circular A", sans-serif;
}

.decor-line-top {
    position: absolute;
    top: -20px;
    left: 40%;
    width: 90px;
    pointer-events: none;
    z-index: 1;
}

.decor-loader-bottom {
    position: absolute;
    bottom: 20px;
    left: 0%;
    width: 290px;
    pointer-events: none;
    z-index: 1;
}

.callback-container {
    max-width: 1601px;
    margin: 0 160px;
    padding: 0 40px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 60px;
    position: relative;
    z-index: 2;
}

.callback-content {
    flex: 0 0 500px;
    display: flex;
    flex-direction: column;
}

.callback-title {
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    text-transform: uppercase;
    color: #000000;
    margin: 0 0 20px 0;
}

.callback-subtitle {
    font-weight: 400;
    font-size: 16px;
    line-height: 100%;
    color: #000000;
    margin: 0 0 30px 0;
}

.callback-form {
    display: flex;
    gap: 15px;
    margin-bottom: 20px;
}

.input-wrapper {
    position: relative;
    flex-grow: 1;
}

.callback-input {
    width: 100%;
    height: 50px;
    border-radius: 100px;
    border: 2px solid #E0E0E0;
    padding: 0 25px;
    font-size: 16px;
    font-family: inherit;
    outline: none;
    box-sizing: border-box;
    transition: border-color 0.3s;
    color: #000;

    &:focus {
        border-color: #ED9121;
    }

    &.input-error {
        border-color: #FF0000;
    }
}

.error-text {
    position: absolute;
    bottom: -20px;
    left: 25px;
    color: #FF0000;
    font-size: 12px;
}

.callback-btn {
    width: 184px;
    height: 50px;
    border-radius: 100px;
    background: #ED9121;
    border: none;
    color: #FFFFFF;
    font-size: 14px;
    font-weight: 600;
    font-family: inherit;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding: 16px 18px;
    transition: filter 0.2s;
    white-space: nowrap;

    &:hover:not(:disabled) {
        filter: brightness(1.1);
    }

    &:disabled {
        opacity: 0.7;
        cursor: not-allowed;
    }
}

.callback-policy {
    font-weight: 400;
    font-size: 12px;
    line-height: 100%;
    color: #888888;
    margin: 0;
    max-width: 300px;
}

.policy-link {
    color: #888888;
    text-decoration: underline;
    text-decoration-style: solid;
    transition: color 0.2s;

    &:hover {
        color: #ED9121;
    }
}

.callback-image-block {
    flex: 1;
    display: flex;
    justify-content: flex-end;

    .callback-img {
        max-width: 100%;
        height: auto;
        border-radius: 20px;
        object-fit: cover;
    }
}

.tel_icon {
    width: 17px;
    height: 17px;
}

@media (max-width: 768px) {
    @font-face {
        font-family: "Euclid Circular A";
        font-weight: 400;
        font-style: normal;
        src: local("Euclid Circular A"),
            local("Euclid-Circular-A"),
            url("../assets/fonts/euclid-circular-a/Euclid\ Circular\ A\ Regular.woff2") format('woff2'),
            url("../assets/fonts/euclid-circular-a/Euclid\ Circular\ A\ Regular.woff") format('woff'),
            url("../assets/fonts/euclid-circular-a/Euclid\ Circular\ A\ Regular.eot") format('eot');
        font-display: swap;
    }

    .callback-section {
        padding-bottom: 0;
    }

    .decor-line-top,
    .decor-loader-bottom {
        display: none;
    }

    .callback-container {
        flex-direction: column;
        text-align: center;
        margin: 0;
        gap: 30px;
        margin-bottom: 30px;
    }

    .callback-title {
        font-size: 26px;
        width: 330px;

        br {
            display: none;
        }
    }

    .callback-subtitle {
        width: 330px;
    }

    .callback-content {
        flex: none;
        width: 100%;
        align-items: center;
    }

    .callback-form {
        flex-direction: column;
        width: 116%;
        max-width: 400px;
    }

    .callback-policy {
        text-align: left;
        margin-left: -20px;
    }

    .callback-btn {
        width: 100%;
    }

    .callback-image-block {
        width: 100%;
        justify-content: center;
    }

    .error-text {
        left: 50%;
        transform: translateX(-50%);
    }
}
</style>