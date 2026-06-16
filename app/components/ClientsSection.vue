<template>
    <section class="clients-section">
        <div class="clients-container">
            <h2 class="clients-title">НАШИ КЛИЕНТЫ</h2>
            <p class="clients-subtitle">
                Наша компания быстро растет и развивается. За время работы мы расширили спектр услуг, приобрели
                множество постоянных клиентов.
            </p>
            <div class="client-group">
                <h3 class="group-title">Коммерческие</h3>
                <div class="logos-row commercial-logos">
                    <img src="../public/logo_cdek.png" alt="СДЭК" class="logo-img logo-cdek" />
                    <img src="../public/logo_megafon.png" alt="Мегафон" class="logo-img logo-megafon" />
                    <img src="../public/logo_rostelecom.png" alt="Ростелеком" class="logo-img logo-rostelecom" />
                    <img src="../public/logo_hh.png" alt="hh.ru" class="logo-img logo-hh" />
                    <img src="../public/logo_maria.png" alt="Мария" class="logo-img logo-maria" />
                </div>
            </div>
            <div class="client-group">
                <h3 class="group-title">Государственные</h3>
                <div class="logos-row state-logos">
                    <img src="../public/logo_mydocs.png" alt="Мои документы" class="logo-img logo-mydocs" />
                    <img src="../public/logo_fns.png" alt="ФНС" class="logo-img logo-fns" />
                    <img src="../public/logo_pfr.png" alt="ПФР" class="logo-img logo-pfr" />
                    <img src="../public/logo_duma.png" alt="Гос. дума" class="logo-img logo-duma" />
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped lang="scss">
.clients-section {
    width: 100%;
    height: 520px;
    background-color: #F5F5F5; // Светлый фон как на макете
    display: flex;
    justify-content: center;
    padding: 60px 0;
    box-sizing: border-box;
}

.clients-container {
    max-width: 1600px;
    width: 100%;
    margin: 0 auto;
    padding: 0 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.clients-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    color: #000;
    text-transform: uppercase;
    margin: 0 0 20px 0;
    letter-spacing: 0%;
    text-align: center;
}

.clients-subtitle {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 100%;
    color: #000;
    margin: 0 0 50px 0;
    text-align: center;
    max-width: 1086px;
}

.client-group {
    width: 100%;
    margin-bottom: 40px;

    &:last-child {
        margin-bottom: 0;
    }
}

.group-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 500;
    font-size: 16px;
    line-height: 100%;
    color: #000;
    margin: 0 0 20px 0;
    text-align: left;
    padding-left: calc(48.7% - 543px);
}

.logos-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    max-width: 1086px;
    margin: 0 215px;
    gap: 42px;
}

.logo-img {
    object-fit: contain;
    display: block;
}

.logo-cdek {
    width: 184px;
    height: 47px;
}

.logo-megafon {
    width: 276px;
    height: 51px;
}

.logo-rostelecom {
    width: 199px;
    height: 57px;
}

.logo-hh {
    width: 86px;
    height: 47px;
}

.logo-maria {
    width: 198px;
    height: 47px;
}

.logo-mydocs {
    width: 182px;
    height: 90px;
}

.logo-fns {
    width: 300px;
    height: 80px;
    margin-left: 50px;
}

.logo-pfr {
    width: 84px;
    height: 87px;
    margin-right: 35px;
}

.logo-duma {
    width: 91px;
    height: 99px;
    margin-right: 20px;
}

@media (max-width: 768px) {
    .clients-title {
        font-size: 26px;
    }

    .clients-subtitle {
        line-height: 120%;
    }

    .logos-row {
        margin: 0;
    }
}
</style>