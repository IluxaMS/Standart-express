<template>
    <section class="blog-section">
        <img src="../public/decor_truck.png" alt="" class="decor decor--truck" />
        <img src="../public/decor_orange_left.png" alt="" class="decor decor--orange-left" />
        <img src="../public/decor_orange_right.png" alt="" class="decor decor--orange-right" />
        <img src="../public/decor_worker.png" alt="" class="decor decor--worker" />

        <div class="blog-container">
            <h2 class="blog-title">Блог</h2>

            <div class="articles-grid">
                <article v-for="(post, index) in currentPosts" :key="index" class="post-card">
                    <div class="post-image-wrapper">
                        <img :src="post.image" :alt="post.title" class="post-image" />
                    </div>
                    <div class="post-meta">
                        <span class="post-date">{{ post.date }}</span>
                        <div class="post-rating">
                            <img src="../public/rating_star.png" alt="star" class="star-icon" />
                            <span>{{ post.rating }}</span>
                        </div>
                    </div>
                    <h3 class="post-title">{{ post.title }}</h3>
                    <p class="post-excerpt">{{ post.excerpt }}</p>
                    <Button label="Читать далее" size="sc" outline @click="$emit('open-article', post)" />
                </article>
            </div>

            <div class="pagination">
                <button class="page-btn page-btn--nav" @click="prevPage" :disabled="currentPage === 1">
                    <img src="../public/arrow_left2.png" alt="<" />
                </button>

                <template v-for="num in visiblePages" :key="num">
                    <button v-if="typeof num === 'number'" class="page-btn"
                        :class="{ 'page-btn--active': currentPage === num }" @click="currentPage = num">
                        {{ num }}
                    </button>
                    <span v-else class="dots">...</span>
                </template>

                <button class="page-btn page-btn--nav" @click="nextPage" :disabled="currentPage === totalPages">
                    <img src="../public/arrow_right2.png" alt=">" />
                </button>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

import blogImg1 from '../public/blog_img_1.jpg';
import blogImg2 from '../public/blog_img_2.jpg';
import blogImg3 from '../public/blog_img_3.jpg';
import blogImg4 from '../public/blog_img_4.jpg';

const basePosts = [
    { id: 1, image: blogImg1, date: '01.03.2023', rating: '4,8/5', title: 'Как перевозить холодильник?', excerpt: 'Холодильник является крупногабаритной бытовой техникой, и его перевозка должна осуществляться по особенным правилам.' },
    { id: 2, image: blogImg2, date: '01.03.2023', rating: '4,8/5', title: 'Как перевозить холодильник?', excerpt: 'Холодильник является крупногабаритной бытовой техникой, и его перевозка должна осуществляться по особенным правилам.' },
    { id: 3, image: blogImg3, date: '01.03.2023', rating: '4,8/5', title: 'Как перевозить холодильник?', excerpt: 'Холодильник является крупногабаритной бытовой техникой, и его перевозка должна осуществляться по особенным правилам.' },
    { id: 4, image: blogImg4, date: '01.03.2023', rating: '4,8/5', title: 'Как перевозить холодильник?', excerpt: 'Холодильник является крупногабаритной бытовой техникой, и его перевозка должна осуществляться по особенным правилам.' }
];

const allPosts = Array.from({ length: 120 }, (_, i) => {
    const pageIndex = Math.floor(i / 8);
    const itemIndex = i % 8;

    const rotatedIndex = (itemIndex + pageIndex) % 4;

    return {
        ...basePosts[rotatedIndex],
        id: i + 1
    };
});

defineEmits<{
    (e: 'open-article', post: typeof basePosts[0]): void
}>();

const currentPage = ref(1);
const itemsPerPage = 8;
const totalPages = Math.ceil(allPosts.length / itemsPerPage);

const currentPosts = computed(() => {
    const start = (currentPage.value - 1) * itemsPerPage;
    return allPosts.slice(start, start + itemsPerPage);
});

const visiblePages = computed(() => {
    const pages: (number | string)[] = [];

    const windowStart = Math.floor((currentPage.value - 1) / 5) * 5 + 1;
    const windowEnd = Math.min(windowStart + 4, totalPages);

    for (let i = windowStart; i <= windowEnd; i++) {
        pages.push(i);
    }

    if (windowEnd < totalPages) {
        pages.push('...');
        pages.push(totalPages);
    }

    return pages;
});

const prevPage = () => { if (currentPage.value > 1) currentPage.value--; };
const nextPage = () => { if (currentPage.value < totalPages) currentPage.value++; };
</script>

<style scoped lang="scss">
.blog-section {
    position: relative;
    width: 100%;
    min-height: 900px;
    background-color: #F5F5F5;
    padding: 60px 0;
    overflow: hidden;
}

.decor {
    position: absolute;
    z-index: 1;
    pointer-events: none;
}

.decor--truck {
    top: 70px;
    left: 0px;
    width: 152px;
    height: 32px;
}

.decor--orange-left {
    bottom: 0;
    left: 130px;
    width: 65px;
    height: auto;
}

.decor--orange-right {
    top: 0;
    right: 100px;
    width: 35px;
    height: auto;
}

.decor--worker {
    bottom: 300px;
    right: 0;
    width: 150px;
    height: auto;
}

.blog-container {
    position: relative;
    z-index: 2;
    max-width: 1245px;
    margin: 0 auto;
    padding: 0 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.blog-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 50px;
    line-height: 100%;
    color: #000;
    margin: 0 0 40px 0;
    width: 100%;
    text-align: left;
}

.articles-grid {
    display: grid;
    grid-template-columns: repeat(4, 285.5px);
    gap: 20px;
    margin-bottom: 50px;
    justify-content: center;
}

.post-card {
    display: flex;
    flex-direction: column;
    width: 285.5px;
    height: 413px;
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

.post-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 18px;
    line-height: 100%;
    color: #000;
    margin: 0 0 10px 0;
}

.post-excerpt {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 14px;
    line-height: 140%;
    color: #000;
    margin: 0 0 20px 0;
    flex-grow: 1;
    opacity: 70%;
}

.pagination {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
}

.page-btn {
    width: 30px;
    height: 30px;
    border-radius: 50%;
    border: 1px solid #CBCBCB;
    background: transparent;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: "Euclid Circular A", sans-serif;
    font-size: 14px;
    color: #000;
    cursor: pointer;
    transition: all 0.2s;

    &:disabled {
        opacity: 0.3;
        cursor: default;
    }

    &--active {
        border-color: #ED9121;
        color: #ED9121;
    }

    &--nav {
        border-color: #CBCBCB;

        img {
            width: 12px;
            height: 12px;
        }
    }

    &:hover:not(&--active):not(:disabled) {
        border-color: #ED9121;
    }
}

.dots {
    color: #000;
    margin: 0 5px;
    font-size: 14px;
}

@media (max-width: 1300px) {
    .articles-grid {
        grid-template-columns: repeat(2, 285.5px);
    }

    .blog-section {
        min-height: auto;
    }
}

@media (max-width: 768px) {
    .blog-section {
        padding: 20px 0;
        min-height: auto;
    }

    .decor {
        display: none;
    }

    .blog-title {
        font-size: 26px;
        margin-bottom: 26px;
    }

    .articles-grid {
        grid-template-columns: 342.5px;
        gap: 10px;
    }

    .post-card {
        width: 285.5px;
        height: 413px;
    }

    .post-image-wrapper {
        width: 343px;
        height: 197px;
    }

    .post-excerpt {
        font-size: 14px;
        line-height: 100%;
    }

    .post-meta {
        gap: 72%;
    }

    .app-button {
        width: 343px !important;
        max-width: none !important;
        height: 50px !important;
        padding: 8px 16px !important;
        font-size: 14px !important;
        margin-bottom: 20px !important;
    }

    .pagination {
        margin-right: 7px;
    }
}
</style>