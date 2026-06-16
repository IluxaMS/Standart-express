<template>
    <div class="article-view">
        <h1 class="article-main-title">{{ post?.title }}</h1>

        <div class="article-layout">
            <aside class="article-sidebar">
                <nav class="toc-nav">
                    <a href="#after-purchase" class="toc-link"
                        :class="{ 'toc-link--active': activeAnchor === 'after-purchase' }"
                        @click.prevent="scrollToAnchor('after-purchase')">
                        Как перевозить холодильник после покупки?
                    </a>

                    <span class="toc-link toc-link--disabled">
                        Упаковка и подготовка холодильников к перевозке
                    </span>

                    <a href="#on-side" class="toc-link" :class="{ 'toc-link--active': activeAnchor === 'on-side' }"
                        @click.prevent="scrollToAnchor('on-side')">
                        Можно ли перевозить холодильник на боку или лёжа?
                    </a>

                    <a v-for="(anchor, idx) in anchors.slice(2)" :key="idx" :href="'#' + anchor.id" class="toc-link"
                        :class="{ 'toc-link--active': activeAnchor === anchor.id }"
                        @click.prevent="scrollToAnchor(anchor.id)">
                        {{ anchor.text }}
                    </a>
                </nav>
            </aside>

            <div class="article-content">
                <div class="article-meta">
                    <span class="post-date">{{ post?.date }}</span>
                    <div class="post-rating">
                        <img src="../public/rating_star.png" alt="star" class="star-icon" />
                        <span>{{ post?.rating }}</span>
                    </div>
                </div>

                <img :src="staticHeroImage" alt="" class="article-hero-image" />

                <p class="article-text intro-text">
                    Холодильник является крупногабаритной бытовой техникой, и его перевозка должна осуществляться по
                    особенным правилам. Невзирая на то, что холодильник внешне выглядит прочно и монолитно, в
                    действительности, он очень хрупкий. При небольшом несоблюдении условий перевозки может произойти
                    его повреждение. А так как, не все хозяева холодильников в курсе данной проблемы, то при
                    перевозке зачастую происходят поломки.<br><br>
                    Каким образом правильно производится перевозка и переноска холодильников будет освещено в данной
                    статье. Принцип действия холодильников, по большому счёту, одинаков, однако не стоит
                    пренебрегать конструктивными особенностями всех холодильников.<br><br>
                    И в каждой инструкции, которая прилагается к оборудованию очень доходчиво описано как правильно
                    осуществляется перевозка определённого холодильника. Однако, общие правила перевозки одинаковые.
                </p>

                <h2 id="after-purchase" class="article-h2">Как перевозить холодильник после покупки?</h2>
                <p class="article-text">
                    Изготовители холодильного оборудования обязуют перевозить его в вертикальном положении стоя. В
                    данной ситуации не осуществляется перемешивание фреона с маслом. В том случае, когда покупатель
                    хочет перевезти холодильник сам, но на горизонтальной стороне холодильника, тогда продавец
                    моментально должен снять гарантию.
                    Необходимо обязательно <span class="highlight-link">перевозить бытовую технику</span> в
                    заводской коробке, защищающей корпус холодильника. Машины, в которых нужно перевозить габаритную
                    технику, обязаны быть обустроены крепёжными элементами в кузове, и перевозить необходимо стоя в
                    вертикальном положении, а не горизонтальной стороной вниз.
                    Рекомендуется после истечения гарантийного термина не выбрасывать заводскую упаковку. Она может
                    понадобиться, когда нужно будет перевезти холодильник следующий раз.
                </p>

                <img src="../public/article_img_2.jpg" alt="" class="article-mid-image desktop-only-img" />

                <h2 id="on-side" class="article-h3">Можно ли перевозить холодильник на боку или лёжа?</h2>
                <p class="article-text">
                    В соответствии с инструкцией, перевозить и переносить холодильные устройства необходимо
                    вертикально стоя, однако, так как холодильник достаточно большого размера, то это не всегда
                    получается, и перевозка холодильника на боку или лёжа допускается в горизонтальной плоскости. В
                    данной ситуации, необходимо тщательно изучить знаки на упаковке, и понять, какими сторонами
                    можно укладывать холодильник, когда планируется его перевезти, горизонтальной или вертикальной
                    сторонами.<br><br>
                    Возможно ли перевозить холодильник на боку, лучше спросить во время приобретения, когда первый
                    раз планируется перевезти его. В ситуации, когда доставку производит магазин, его работники
                    выполняют основное правило – лёжа перевозить нельзя, только в вертикальном положении.<br><br>
                    Изготовители холодильников не рекомендуют перевозить холодильник лёжа на боку по следующим
                    причинам:
                </p>
                <ol class="custom-list">
                    <li>Могут повредиться двери и ручки при перевозке в положении лёжа. Возможно холодильник станет
                        не таким герметичным, когда будет произведена перевозка холодильника. Лёжа на дверцах нельзя
                        производить перевозку;</li>
                    <li>Возможно масло перемешается с фреоном, если холодильник будет находиться в лежачем
                        положении;</li>
                    <li>Нарушения рабочих частей холодильников. Такие, как закрепления компрессора, патрубка, а
                        также может разорваться электропровод;</li>
                    <li>Возможно соскакивание пружин;</li>
                    <li>Продавливание теплоизоляции.</li>
                </ol>
                <p class="article-text">
                    Лёжа на боку, вне зависимости на каком боку, есть вероятность появления повреждений.
                    Минимизировать риски возможно, определившись, где находится нагнетательная трубка, исходящая из
                    компрессора. При перевозке в лежачем положении необходимо, чтоб данная трубка располагалась в
                    верхней части. Тогда масло может не попасть в контур. Когда будет выполнена перевозка,
                    необходимо установить холодильник, и не подключать его более 4 часов, дать маслу стечь.<br><br>
                    И ещё одна рекомендация. Не стоит производить наклон холодильников при перевозке более чем на 45
                    градусов. И, если производить наклон холодильников, когда производиться перевозка, то в сторону
                    мотора. А холодильники, работающие по системе «ноу фрост», в обязательном порядке перевозить в
                    вертикальном положении.
                </p>

                <h2 id="fastening" class="article-h4">Как крепить холодильник в автомобиле?</h2>
                <p class="article-text">
                    Основной целью при перевозке холодильников в любом положении должно быть их фиксирование, и
                    исключение передвижения холодильников в кузове при перевозке. Чаще всего для закрепления
                    холодильников применяются различные специальные приспособления для крепления габаритной техники.
                    Если используются различные опоры для фиксирования холодильников, тогда необходимо произвести
                    добавочную защиту в местах соприкосновения холодильников и опор. Немаловажным при перевозке
                    является то, что под холодильник необходимо проложить подкладку, для более мягкой перевозки, а
                    также гашения вибрации и предотвращения передвижения холодильников по кузову во время перевозки.
                    Желательно, чтобы фиксация была очень жёсткой.
                </p>

                <h2 id="manual-moving" class="article-h5">Перемещение холодильника вручную</h2>
                <p class="article-text">
                    Когда перевозка выполнена, требуется перенести и установить холодильник. Как правило, переноска
                    холодильников осуществляется минимум двумя людьми.
                    При переноске холодильников желательно использовать такелажные ремни, и необходимо соблюдать
                    следующие правила:
                </p>
                <ol class="custom-list">
                    <li>Перенос холодильников должен осуществляться очень осторожно;</li>
                    <li>Не стаскивать холодильник с кузова машины;</li>
                    <li>Не укладывать себе на спину;</li>
                    <li>Желательно использовать специальные подъёмные механизмы;</li>
                    <li>Переноска должна осуществляться в вертикальном положении стоя, и компрессор должен
                        находиться в нижней части. По утверждённым условиям перемещения холодильники перевозить
                        нужно в положении вертикально;</li>
                    <li>Не нести, держась за двери и ручки холодильников.</li>
                </ol>
                <p class="article-text">
                    У большинства нынешних холодильников присутствуют колёса, с помощью которые можно их катить по
                    ровному месту, немного наклоняя холодильник. Таким образом возможно переместить холодильник на
                    улице или в квартире.
                    Установив холодильник на место, где он будет стоять постоянно, необходимо дать холодильнику
                    принять температурные параметры помещения. Если <span class="highlight-link">перевозка
                        холодильников</span> осуществляется зимой, желательно, чтобы холодильник «отогрелся» минимум
                    5 часов, а лучше, если холодильник постоит не включенным более 8 часов. Требуется осмотреть
                    холодильник, и если есть какая-то влага, то просушить холодильник, как изнутри, так и снаружи.
                </p>
            </div>
        </div>

        <div class="other-articles">
            <h2 class="other-title">Другие статьи</h2>
            <div class="articles-grid">
                <article v-for="(item, index) in otherPosts" :key="index" class="post-card">
                    <div class="post-image-wrapper">
                        <img :src="item.image" :alt="item.title" class="post-image" />
                    </div>
                    <div class="post-meta">
                        <span class="post-date">{{ item.date }}</span>
                        <div class="post-rating">
                            <img src="../public/rating_star.png" alt="star" class="star-icon" />
                            <span>{{ item.rating }}</span>
                        </div>
                    </div>
                    <h3 class="post-title">{{ item.title }}</h3>
                    <p class="post-excerpt">{{ item.excerpt }}</p>
                    <Button label="Читать далее" size="sc" outline @click="$emit('open-article', item)" />
                </article>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

import blogImg1 from '../public/blog_img_1.jpg';
import blogImg2 from '../public/blog_img_2.jpg';
import blogImg3 from '../public/blog_img_3.jpg';
import blogImg4 from '../public/blog_img_4.jpg';

const props = defineProps<{
    post: {
        id: number;
        image: string;
        date: string;
        rating: string;
        title: string;
        excerpt: string;
    } | null
}>();

defineEmits<{
    (e: 'open-article', post: any): void
}>();

const staticHeroImage = blogImg3;

const activeAnchor = ref('');

const anchors = [
    { id: 'after-purchase', text: 'Как перевозить холодильник после покупки?' },
    { id: 'on-side', text: 'Можно ли перевозить холодильник на боку или лёжа?' },
    { id: 'fastening', text: 'Как крепить холодильник в автомобиле?' },
    { id: 'manual-moving', text: 'Перемещение холодильника вручную' }
];

const otherPosts = [
    { id: 1, image: blogImg1, date: '01.03.2023', rating: '4,8/5', title: 'Как перевозить холодильник?', excerpt: 'Холодильник является крупногабаритной бытовой техникой, и его перевозка должна осуществляться по особенным правилам.' },
    { id: 2, image: blogImg2, date: '01.03.2023', rating: '4,8/5', title: 'Как перевозить холодильник?', excerpt: 'Холодильник является крупногабаритной бытовой техникой, и его перевозка должна осуществляться по особенным правилам.' },
    { id: 3, image: blogImg3, date: '01.03.2023', rating: '4,8/5', title: 'Как перевозить холодильник?', excerpt: 'Холодильник является крупногабаритной бытовой техникой, и его перевозка должна осуществляться по особенным правилам.' },
    { id: 4, image: blogImg4, date: '01.03.2023', rating: '4,8/5', title: 'Как перевозить холодильник?', excerpt: 'Холодильник является крупногабаритной бытовой техникой, и его перевозка должна осуществляться по особенным правилам.' }
];

const scrollToAnchor = (id: string) => {
    const element = document.getElementById(id);
    if (element) {
        element.scrollIntoView({ behavior: 'smooth', block: 'start' });
        activeAnchor.value = id;
    }
};

const handleScroll = () => {
    let currentId = '';
    anchors.forEach(anchor => {
        const element = document.getElementById(anchor.id);
        if (element) {
            const rect = element.getBoundingClientRect();
            if (rect.top <= 150) currentId = anchor.id;
        }
    });
    if (currentId) activeAnchor.value = currentId;
};

onMounted(() => window.addEventListener('scroll', handleScroll));
onUnmounted(() => window.removeEventListener('scroll', handleScroll));
</script>

<style scoped lang="scss">
.article-view {
    width: 100%;
    max-width: 1600px;
    margin: 0;
    margin-left: 306px;
    padding: 0 20px;
}

.article-main-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 50px;
    line-height: 100%;
    color: #000;
    margin: 40px 0 30px 0;
    white-space: nowrap;
    width: 100%;
}

.article-layout {
    display: flex;
    gap: 40px;
    margin-bottom: 70px;
    align-items: flex-start;
}

.article-sidebar {
    width: 183px;
    flex-shrink: 0;
    position: sticky;
    top: 100px;
    margin-top: 42px;
}

.toc-nav {
    display: flex;
    flex-direction: column;
    gap: 15px;
}

.toc-link {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 14px;
    color: #000;
    text-decoration: underline;
    text-decoration-thickness: 1px;
    transition: color 0.2s;
    cursor: pointer;

    &--active {
        color: #ED9121;
    }

    &--disabled {
        &:hover {
            color: #ED9121;
        }
    }
}

.article-content {
    width: 716px;
    flex-shrink: 0;
}

.article-meta {
    display: flex;
    align-items: center;
    gap: 20px;
    margin-bottom: 30px;
}

.post-date {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 14px;
    color: #000;
    opacity: 50%;
}

.post-rating {
    display: flex;
    align-items: center;
    gap: 5px;
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 500;
    font-size: 16px;
    color: #000;
}

.star-icon {
    width: 16px;
    height: 16px;
}

.article-hero-image {
    width: 100%;
    max-width: 716px;
    height: auto;
    aspect-ratio: 692 / 315;
    object-fit: cover;
    border-radius: 20px;
    margin: 0 0 30px 0;
    display: block;
}

.article-mid-image {
    width: 100%;
    max-width: 716px;
    height: auto;
    aspect-ratio: 692 / 315;
    object-fit: cover;
    border-radius: 20px;
    margin: 30px 0;
    display: block;
}

.intro-text {
    margin-bottom: 40px;
    text-align: justify;
}

.article-h2 {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 32px;
    line-height: 100%;
    color: #000;
    margin: 40px 0 20px 0;
}

.article-h3 {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 24px;
    line-height: 100%;
    color: #000;
    margin: 40px 0 20px 0;
}

.article-h4 {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 20px;
    line-height: 100%;
    color: #000;
    margin: 40px 0 20px 0;
}

.article-h5 {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    font-size: 18px;
    line-height: 100%;
    color: #000;
    margin: 40px 0 20px 0;
}

.article-text {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 160%;
    color: #000;
    margin: 0 0 20px 0;
    text-align: left;
}

.highlight-link {
    text-decoration: underline;
    color: #ED9121;
    cursor: pointer;
}

.custom-list {
    list-style: none;
    counter-reset: my-counter;
    padding-left: 0;
    margin: 0 0 20px 0;

    li {
        position: relative;
        padding-left: 20px;
        margin-bottom: 10px;
        font-family: "Euclid Circular A", sans-serif;
        font-weight: 400;
        font-size: 16px;
        line-height: 160%;
        color: #000;
        margin-left: 10px;

        &::before {
            counter-increment: my-counter;
            content: counter(my-counter) ".";
            position: absolute;
            left: 0;
            top: 0;
        }
    }
}

.other-articles {
    text-align: center;
    margin-right: 30%;
}

.other-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    color: #000;
    text-transform: uppercase;
    margin: 0 0 40px 0;
}

.articles-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 25px;
    justify-content: center;
    margin-bottom: 50px;
}

.post-card {
    display: flex;
    flex-direction: column;
    width: 285.5px;
    height: 413px;
    margin: 0 auto;
}

.post-image-wrapper {
    width: 285px;
    height: 197px;
    border-radius: 20px;
    overflow: hidden;
    margin-bottom: 15px;
    flex-shrink: 0;
}

.post-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.post-meta {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
}

.post-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 18px;
    line-height: 100%;
    color: #000;
    margin: 0 0 10px 0;
    text-align: left;
}

.post-excerpt {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 14px;
    line-height: 140%;
    color: #000;
    margin: 0 0 20px 0;
    flex-grow: 1;
    text-align: left;
}

.desktop-only-img {
    display: block;
}

@media (max-width: 1200px) {
    .articles-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (max-width: 1024px) {
    .article-view {
        padding: 0 20px;
        margin-left: 0px;
    }

    .article-main-title {
        font-size: 32px;
        white-space: normal;
        margin-bottom: 20px;
    }

    .article-layout {
        flex-direction: column;
        gap: 20px;
        align-items: stretch;
        margin-bottom: 0px;
    }

    .article-hero-image {
        height: 265px;
    }

    .article-text {
        text-align: justify;
    }

    .article-meta {
        margin-bottom: 20px;
    }

    .article-sidebar {
        width: 83%;
        position: static;
        order: -1;
        margin-bottom: 20px;
        margin-top: 25px;
        margin-left: 15px;

        .toc-nav {
            flex-direction: row;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: flex-start;
        }

        .toc-link {
            font-size: 12px;
        }
    }

    .article-content {
        width: 100%;
    }

    .article-h2 {
        font-size: 24px;
    }

    .article-h3 {
        font-size: 20px;
    }

    .desktop-only-img {
        display: none;
    }

    .other-title {
        font-size: 32px;
        text-transform: none;
    }

    .articles-grid {
        grid-template-columns: 1fr;
        gap: 26px;
        justify-items: center;
    }

    .post-card {
        width: 100%;
        max-width: 343px;
        height: auto;
        min-height: 413px;
    }

    .post-image-wrapper {
        width: 100%;
        max-width: 343px;
        height: 197px;
    }

    .app-button {
        width: 100%;
        max-width: 343px;
        justify-content: center;
    }

    .other-articles {
        margin-right: 0px;
        padding-top: 20px;
    }
}
</style>