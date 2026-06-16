<template>
    <section class="faq-section">
        <div class="faq-container">
            <h2 class="faq-title">ЧАСТО ЗАДАВАЕМЫЕ ВОПРОСЫ</h2>

            <div class="faq-list">
                <div v-for="(item, index) in visibleItems" :key="index" class="faq-item"
                    :class="{ 'is-open': openIndex === index }">
                    <button class="faq-question" @click="toggleAccordion(index)">
                        <span class="question-text">{{ item.question }}</span>
                        <div class="icon-wrapper">
                            <img v-if="openIndex === index" src="../public/minus2.png" alt="-" class="faq-icon" />
                            <img v-else src="../public/plus2.png" alt="+" class="faq-icon" />
                        </div>
                    </button>

                    <div class="faq-answer-wrapper">
                        <div class="faq-answer" v-html="item.answer"></div>
                    </div>
                </div>
            </div>

            <div class="faq-footer">
                <button class="show-all-btn" @click="toggleShowAll">
                    {{ isShowAll ? 'Скрыть' : 'Показать все' }}
                </button>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

const openIndex = ref<number | null>(0);
const isShowAll = ref(false);

const allQuestions = [
    {
        question: "Как узнать стоимость погрузочно-разгрузочных работ?",
        answer: "В онлайн-курс входят 5 тренировок с видео, полезные материалы по основам стретчинга и личный кабинет с трекерами калорий и воды, а также сборник простых и вкусных ПП рецептов"
    },
    {
        question: "Какие люди у Вас работают?",
        answer: "У нас работают крепкие мужчины, граждане РФ, в возрасте 20-55 лет."
    },
    {
        question: "Вы работаете по безналичному расчету?",
        answer: "От коммерческих и государственных организаций оплату принимаем исключительно на расчетный счет."
    },
    {
        question: "Вы работаете с НДС?",
        answer: "Да, мы принимаем оплату, как с НДС, так и без НДС."
    },
    {
        question: "Как оплачивается заказ?",
        answer: "Мы работаем по системе постоплаты: выполняем определенный объем по квартирному, офисному переезду, такелажу и т.п., после этого выставляем счет на оплату."
    },
    {
        question: "У вас есть свой типовой договор?",
        answer: "Да. Вы можете запросить его. Если вы хотите подписать свой договор — присылайте. Мы проверим его в течение 30 минут, если все в порядке, заполним и подпишем."
    },
    {
        question: "Вы несете материальную ответственность?",
        answer: "Да, конечно. Пункт о материальной ответственности прописан в типовом договоре."
    },
    {
        question: "Как быть, если наша компания долго согласовывает договор, а грузчики нужны уже срочно?",
        answer: "В таких ситуациях мы идем на встречу Клиентам, грузчикам достаточно будет подписать акт на месте проведения работ."
    },
    {
        question: "Как быстро смогут приехать грузчики с момента заявки?",
        answer: "Среднее время прибытия грузчиков на заказ 45 минут."
    },
    {
        question: "У нас тендер, Вы принимаете участие в тендерах?",
        answer: "Да, конечно. У нас есть тендерные специалисты, которые подготовят всю необходимую документацию."
    },
    {
        question: "У нас намечается переезд, вы можете кого-нибудь прислать, чтобы посчитали стоимость?",
        answer: "Да. У нас есть специалисты, которые выезжают к Клиенту и составляют смету. Это удобно тем, что вы сразу узнаете окончательную стоимость офисного или квартирного переезда — она будет прописана в договоре."
    },
    {
        question: "Можно ли приобрести упаковочные материалы, не пользуясь Вашими услугами?",
        answer: "Мы не занимаемся продажей упаковочных материалов. Мы закупаем упаковочный материал в тех объемах, который нам необходим при квартирных и офисных переездах наших Клиентов."
    },
    {
        question: "Можете подробнее рассказать об услуге «комплексный переезд»?",
        answer: "Любой переезд состоит из нескольких этапов. Услуга «комплексный переезд» включает в себя все этапы «под ключ». Все работы производятся нашими специалистами: Разбираем мебель и демонтируем бытовую технику. Сами упаковываем вещи для перевозки. Грузим вещи в машину. Перевозим."
    },
    {
        question: "Нам нужно оценить стоимость такелажных работ, как это сделать?",
        answer: "Вы можете отправить всю информацию на почту: <a href='mailto:info@standart-express.ru' class='email-link'>info@standart-express.ru</a><br><br>Если полученной информации будет достаточно для просчета, оператор назовет стоимость работ. Или Вы так же можете заказать бесплатную услугу: выезд инженера оценщика."
    },
    {
        question: "Что входит в услуги грузчиков?",
        answer: "В услуги грузчиков входят: погрузка и разгрузка различных грузов (мебель, бытовая техника, стройматериалы), их перемещение по территории, упаковка, разборка и сборка мебели, вывоз мусора и такелажные работы для тяжёлых и нестандартных объектов. Мы также можем предоставить дополнительные услуги, такие как предоставление упаковочных материалов и помощь при инвентаризациях."
    },
    {
        question: "Какова стоимость услуг грузчиков?",
        answer: "Стоимость услуг грузчиков зависит от типа работы, объёма и сложности задачи. Например, почасовая ставка обычно начинается от 249 рублей в час. Для переездов или сложных задач стоимость рассчитывается индивидуально, в зависимости от расстояния, объёма работы и дополнительных услуг. Мы всегда уточняем цену заранее, чтобы вы знали, за что платите."
    }
];

const visibleItems = computed(() => {
    return isShowAll.value ? allQuestions : allQuestions.slice(0, 8);
});

const toggleAccordion = (index: number) => {
    openIndex.value = openIndex.value === index ? null : index;
};

const toggleShowAll = () => {
    isShowAll.value = !isShowAll.value;
    if (!isShowAll.value && openIndex.value !== null && openIndex.value >= 8) {
        openIndex.value = null;
    }
};
</script>

<style scoped lang="scss">
.faq-section {
    width: 100%;
    min-height: 900px;
    background-color: #F5F5F5;
    display: flex;
    justify-content: center;
    padding: 80px 0;
    font-family: "Euclid Circular A", sans-serif;
}

.faq-container {
    width: 100%;
    max-width: 1600px;
    padding: 0 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.faq-title {
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    text-transform: uppercase;
    color: #000000;
    margin: 0 0 50px 0;
    text-align: center;
}

.faq-list {
    width: 100%;
    max-width: 1171px;
    display: flex;
    flex-direction: column;
    gap: 16px;
}

.faq-item {
    background-color: #FFFFFF;
    border-radius: 20px;
    overflow: hidden;
    transition: box-shadow 0.3s ease;

    &.is-open {
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
    }
}

.faq-question {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 25px 32px;
    background: none;
    border: none;
    cursor: pointer;
    text-align: left;

    .question-text {
        font-weight: 700;
        font-size: 16px;
        line-height: 140%;
        color: #000000;
        padding-right: 20px;
    }
}

.icon-wrapper {
    flex-shrink: 0;
    width: 20px;
    height: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.faq-icon {
    width: 20px;
    height: 20px;
    object-fit: contain;
}

.faq-answer-wrapper {
    display: grid;
    grid-template-rows: 0fr;
    transition: grid-template-rows 0.4s ease-out;

    .faq-item.is-open & {
        grid-template-rows: 1fr;
    }
}

.faq-answer {
    overflow: hidden;
    padding: 0 32px;
    opacity: 0;
    transform: translateY(-10px);
    transition: opacity 0.4s ease, transform 0.4s ease, padding 0.4s ease;

    .faq-item.is-open & {
        opacity: 1;
        transform: translateY(0);
        padding: 0 32px 30px 32px;
    }

    p {
        font-weight: 400;
        font-size: 16px;
        line-height: 180%;
        color: #4A4A4A;
        margin: 0;
    }

    .email-link {
        color: #ED9121;
        text-decoration: underline;
        transition: color 0.2s;
    }
}

.faq-footer {
    margin-top: 40px;
}

.show-all-btn {
    width: 127px;
    height: 50px;
    border-radius: 100px;
    border: 1px solid #ED9121;
    background: transparent;
    color: #ED9121;
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 14px;
    line-height: 100%;
    cursor: pointer;
    transition: all 0.3s ease;
    display: flex;
    align-items: center;
    justify-content: center;

    &:hover {
        background: #ED9121;
        color: #FFFFFF;
    }
}

@media (max-width: 768px) {
    .faq-title {
        font-size: 26px;
        line-height: 33px;
    }

    .show-all-btn {
        width: 300px;
    }

    .faq-question {
        padding: 20px;
    }

    .faq-answer {
        padding: 0 20px;

        .faq-item.is-open & {
            padding: 0 20px 20px 20px;
        }
    }
}
</style>