<template>
    <section class="final-callback-section">
        <img src="../public/decor-orange-line.png" alt="" class="decor-orange-line" />
        <img src="../public/decor-truck-line.png" alt="" class="decor-truck-line" />
        <img src="../public/decor-right-line.png" alt="" class="decor-right-line" />
        <img src="../public/decor-quotes.png" alt="" class="decor-quotes" />

        <div class="callback-container">
            <div class="callback-content">
                <img src="../public/rustam_photo_mob.png" alt="Рустам" class="manager-img_mob">
                <h2 class="manager-title">
                    Я - Рустам,<br class="br_mob"> руководитель отдела<br class="br_mob"> по работе с<br class="br_mob">
                    клиентами.
                </h2>

                <div class="manager-desc">
                    <p>Спасибо, что просмотрели сайт до конца!</p>
                    <p class="line_2">Оставьте заявку в этой форме и<br class="br_mob"> получите скидку</p>
                    <p>Укажите номер телефона, мы перезвоним вам в течение 1-ой минуты</p>
                </div>

                <form class="callback-form" @submit.prevent="submitForm">
                    <div class="input-wrapper">
                        <input type="tel" placeholder="+7" v-model="phone" @input="validatePhone"
                            :class="{ 'input-error': phoneError }" class="callback-input">
                        <span v-if="phoneError" class="error-text">Ошибка</span>
                    </div>

                    <button type="submit" class="callback-btn" :disabled="phoneError || phone.length < 10">
                        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path
                                d="M22 16.92V19.92C22.0011 20.1985 21.9441 20.4742 21.8325 20.7293C21.7209 20.9845 21.5573 21.2136 21.3521 21.4019C21.1468 21.5901 20.9046 21.7335 20.6407 21.8227C20.3769 21.9119 20.0974 21.9451 19.82 21.92C16.7428 21.5856 13.787 20.5341 11.19 18.85C8.77382 17.3147 6.72533 15.2662 5.19 12.85C3.50564 10.2531 2.45425 7.29743 2.12 4.22C2.09506 3.94266 2.12827 3.66319 2.21747 3.39932C2.30667 3.13546 2.44997 2.89334 2.63818 2.68808C2.82639 2.48282 3.05541 2.31921 3.31051 2.20762C3.56562 2.09603 3.84135 2.03896 4.12 2.04H7.12C7.60584 2.03896 8.07382 2.21517 8.43622 2.53564C8.79862 2.85611 9.03144 3.2992 9.09 3.78C9.20507 4.68007 9.43507 5.56329 9.77 6.4C9.90172 6.72526 9.94217 7.07845 9.88662 7.41825C9.83107 7.75805 9.68183 8.07064 9.455 8.32L8.09 9.68C9.51354 12.1825 11.5675 14.2365 14.07 15.66L15.43 14.29C15.6794 14.0632 15.9919 13.9139 16.3317 13.8584C16.6715 13.8028 17.0247 13.8433 17.35 13.97C18.1867 14.3049 19.0699 14.5349 19.97 14.65C20.4553 14.7123 20.9013 14.9503 21.2238 15.3187C21.5463 15.6871 21.7228 16.1608 21.72 16.65V16.92Z"
                                stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
                        </svg>
                        Перезвоните мне
                    </button>
                </form>

                <p class="callback-policy">
                    Отправляя заявку, вы соглашаетесь с <a href="/public/policy.txt" target="_blank"
                        class="policy-link">политикой обработки персональных данных</a>
                </p>
            </div>
        </div>
        <div class="manager-image-block">
            <img src="../public/rustam_photo.png" alt="Рустам" class="manager-img">
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
        alert('Заявка отправлена! Рустам перезвонит вам.');
    }
};
</script>

<style scoped lang="scss">
.final-callback-section {
    position: relative;
    width: 100%;
    min-height: 500px;
    background-color: #FFFFFF;
    overflow: hidden;
    font-family: "Euclid Circular A", sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 50px;
}

.decor-orange-line {
    position: absolute;
    left: 8%;
    top: 25%;
    transform: translateY(-50%);
    width: 70px;
    height: 265px;
    pointer-events: none;
    z-index: 1;
}

.decor-truck-line {
    position: absolute;
    left: 0;
    bottom: 10%;
    width: 200px;
    height: 53px;
    pointer-events: none;
    z-index: 1;
}

.decor-right-line {
    position: absolute;
    right: 29%;
    top: 54%;
    width: 221px;
    height: 59px;
    pointer-events: none;
    z-index: 1;
}

.decor-quotes {
    position: absolute;
    left: 16%;
    top: 20.5%;
    width: 30px;
    height: 31px;
    pointer-events: none;
    z-index: 2;
}

.callback-container {
    position: relative;
    z-index: 3;
    width: 100%;
    max-width: 1300px;
    padding: 0 40px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 60px;
}

.callback-content {
    flex: 0 0 640px;
    display: flex;
    flex-direction: column;
    padding-left: 80px;
    margin-left: 200px;
}

.manager-title {
    font-weight: 700;
    font-size: 32px;
    line-height: 130%;
    color: #000000;
    margin: 0 0 30px 0;
    max-width: 594px;
}

.manager-desc {
    font-weight: 400;
    font-size: 16px;
    line-height: 100%;
    color: #000000;
    margin: 0 0 30px 0;

    p {
        margin: 0 0 10px 0;

        &:last-child {
            margin-bottom: 0;
        }
    }

    .line_2 {
        margin: 0 0 20px 0;
    }
}

.callback-form {
    display: flex;
    gap: 15px;
    margin-bottom: 20px;
}

.input-wrapper {
    position: relative;
    flex-grow: 1;
    max-width: 350px;
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
    margin-bottom: 6px;
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
    transition: color 0.2s;

    &:hover {
        color: #ED9121;
    }
}

.manager-image-block {
    flex-shrink: 0;
    margin-right: 8%;
    z-index: 2;

    .manager-img {
        width: 350px;
        height: auto;
        border-radius: 20px;
        object-fit: cover;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
    }
}

.manager-img_mob,
.br_mob {
    display: none;
}

@media (max-width: 768px) {
    .callback-container {
        flex-direction: column;
        text-align: center;
        margin-left: 27px;
    }

    .manager-img {
        display: none;
    }

    .manager-img_mob,
    .br_mob {
        display: block;
    }

    .callback-content {
        flex: none;
        width: 100%;
        align-items: center;
        padding-left: 0;
        margin: 0;
    }

    .manager-title,
    .manager-desc,
    .callback-policy {
        text-align: center;
        min-width: 121%;
    }

    .manager-title {
        margin-top: 20px;
        line-height: 100%;
    }

    .callback-form {
        flex-direction: column;
        width: 118%;
        max-width: 400px;
    }

    .callback-btn {
        width: 100%;
    }

    .callback-policy {
        text-align: left;
        margin-left: 20px;
    }

    .manager-image-block {
        margin-top: 40px;
    }

    .decor-quotes,
    .decor-orange-line,
    .decor-truck-line,
    .decor-right-line {
        display: none;
    }
}
</style>