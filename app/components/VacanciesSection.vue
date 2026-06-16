<template>
    <section class="vacancies-section">
        <div class="vacancies-container">
            <div class="section-header">
                <h2 class="section-title">ВАКАНСИИ</h2>
                <p class="section-subtitle">Ведём постоянный набор</p>
            </div>

            <div class="vacancies-grid">

                <article class="vacancy-card">
                    <div class="card-image-wrapper">
                        <img src="../public/vacancy_loaders.jpg" alt="Грузчики" class="card-image" />
                    </div>
                    <div class="card-content">
                        <h3 class="card-title">Грузчики</h3>
                        <h4 class="card-subtitle">Обязанности:</h4>
                        <ul class="custom-list">
                            <li>Погрузочно-разгрузочные работы;</li>
                            <li>Погрузка/разгрузка грузовых машин;</li>
                            <li>Складские работы;</li>
                            <li>Работа на строительных объектах;</li>
                            <li>Такелаж;</li>
                            <li>Демонтаж;</li>
                            <li>Подсобные работы.</li>
                        </ul>
                    </div>
                </article>

                <article class="vacancy-card">
                    <div class="card-image-wrapper">
                        <img src="../public/vacancy_general_workers.jpg" alt="Разнорабочие" class="card-image" />
                    </div>
                    <div class="card-content">
                        <h3 class="card-title">Разнорабочие</h3>
                        <h4 class="card-subtitle">Требования:</h4>
                        <ul class="custom-list">
                            <li>Пунктуальность;</li>
                            <li>Можно без опыта работы (обучение в процессе);</li>
                            <li>Физическая активность;</li>
                            <li>Вежливость и аккуратность.</li>
                        </ul>
                    </div>
                </article>

                <article class="vacancy-card">
                    <div class="card-image-wrapper">
                        <img src="../public/vacancy_riggers.jpg" alt="Такелажники" class="card-image" />
                    </div>
                    <div class="card-content">
                        <h3 class="card-title">Такелажники</h3>
                        <h4 class="card-subtitle">Условия:</h4>
                        <ul class="custom-list">
                            <li>Почасовая или посменная оплата;</li>
                            <li>Стабильные выплаты, еженедельно без задержек;</li>
                            <li>Работа разъездного характера в разных районах.</li>
                        </ul>
                    </div>
                </article>

            </div>
        </div>
    </section>
</template>


<style scoped lang="scss">
.vacancies-section {
    width: 100%;
    min-height: 724px;
    background-color: #F5F5F5;
    padding: 60px 0;
    display: flex;
    justify-content: center;
}

.vacancies-container {
    max-width: 1600px;
    width: 100%;
    margin: 0 auto;
    padding: 0 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.section-header {
    text-align: center;
    margin-bottom: 50px;
}

.section-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    color: #000;
    text-transform: uppercase;
    margin: 0 0 10px 0;
    letter-spacing: 0%;
}

.section-subtitle {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 100%;
    color: #000;
    margin: 0;
    letter-spacing: 0%;
}

.vacancies-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 70px;
    width: 100%;
    max-width: 1100px;
}

.vacancy-card {
    background-color: #FFFFFF;
    border-radius: 20px;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.03);
}

.card-image-wrapper {
    width: 100%;
    height: 210px;
    overflow: hidden;
}

.card-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
}

.card-content {
    padding-top: 18px;
    display: flex;
    flex-direction: column;
    flex-grow: 1;
}

.card-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 20px;
    line-height: 100%;
    color: #000;
    margin: 0 0 20px 0;
    letter-spacing: 0%;
}

.card-subtitle {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 500;
    font-size: 16px;
    line-height: 100%;
    color: #000;
    margin: 0 0 15px 0;
    letter-spacing: 0%;
}

.custom-list {
    list-style: none;
    padding-left: 8px;
    margin: 0;
    display: flex;
    flex-direction: column;
    gap: 3px;
}

.custom-list li {
    position: relative;
    padding-left: 13px;
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 500;
    font-size: 14px;
    line-height: 140%;
    color: #333;
    letter-spacing: 0%;
}

.custom-list li::before {
    content: '';
    position: absolute;
    left: 0;
    top: 8px;
    width: 4px;
    height: 4px;
    background-color: #000;
    border-radius: 50%;
}

@media (max-width: 1024px) {
    .vacancies-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (max-width: 768px) {
    .vacancies-section {
        padding: 40px 0;
        min-height: auto;
    }

    .section-title {
        font-size: 32px;
    }

    .vacancies-grid {
        grid-template-columns: 1fr;
        gap: 20px;
        max-width: 400px;
    }

    .card-image-wrapper {
        height: 200px;
    }
}
</style>