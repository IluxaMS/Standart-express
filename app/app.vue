<template>
    <div class="app-wrapper">
        <Header @navigate="setRoute" />
        <Catalog @navigate="setRoute" />
        <template v-if="currentRoute === 'home'">
            <HeroSection title-line-1="Услуги грузчиков" title-line-2="в" title-line-3="Москве"
                title-line-4="от 249₽/час" :hero-image-src="heroImage" hero-image-alt="Грузчик на складе" />
            <AdvantagesSection class="desktop-only" />
            <div class="main-content">
                <VideoPromoSection class="block-video" />
                <GuaranteeSection class="block-guarantee" />
            </div>
            <PopularServices />
            <OnlineCalculator id="online-calculator" />
            <PhotoGallery />
            <ReviewsVideoSection />
            <CallbackSection />
            <AdditionalServices />
            <RecommendationLetters />
            <FaqSection />
            <FinalCallbackSection />
            <ServicesTextSection />
        </template>

        <template v-else-if="currentRoute === 'company'">
            <CompanyInfoSection />
            <AdvantagesSection2 />
            <MissionSection />
            <ValuesSection />
            <DownloadsSection />
            <RecommendationLetters />
            <ClientsSection />
        </template>

        <template v-else-if="currentRoute === 'vacancies'">
            <HiringSection />
            <VacanciesSection />
            <RecommendationLetters />
        </template>

        <template v-else-if="currentRoute === 'news'">
            <div v-if="!isArticleOpen">
                <BlogSection @open-article="openArticle" />
                <CallbackSection />
            </div>
            <ArticleView v-else :post="currentPost" @open-article="openArticle" />
        </template>

        <template v-else-if="currentRoute === 'contacts'">
            <ContactsSection />
            <CoverageSection />
            <FinalCallbackSection />
        </template>

        <template v-else-if="currentRoute === 'loaders'">
            <HeroSection title-line-1="Услуги грузчиков" title-line-2="в" title-line-3="Москве"
                title-line-4="от 249₽/час" :hero-image-src="heroImage2" hero-image-alt="Услуги грузчиков" />
            <AdvantagesSection class="desktop-only" />
            <div class="main-content">
                <VideoPromoSection class="block-video" />
                <GuaranteeSection class="block-guarantee" />
            </div>
            <PopularServices />
            <OnlineCalculator id="online-calculator" />
            <PhotoGallery />
            <ReviewsVideoSection />
            <CallbackSection />
            <AdditionalServices />
            <RecommendationLetters />
            <FaqSection />
            <FinalCallbackSection />
            <ServicesTextSection />
        </template>

        <template v-else-if="currentRoute === 'moves'">
            <HeroSection title-line-1="Переезд с грузчиками" title-line-2="в" title-line-3="Москве"
                title-line-4="от 249₽/час" :hero-image-src="heroImage4" :show-br-desc="false" :show-br-mob="true"
                hero-image-alt="Переезд с грузчиками" />
            <AdvantagesSection class="desktop-only" />
            <div class="main-content">
                <VideoPromoSection class="block-video" />
                <GuaranteeSection class="block-guarantee" />
            </div>
            <PopularServices />
            <OnlineCalculator id="online-calculator" />
            <PhotoGallery />
            <ReviewsVideoSection />
            <CallbackSection />
            <AdditionalServices />
            <RecommendationLetters />
            <FaqSection />
            <FinalCallbackSection />
            <ServicesTextSection />
        </template>

        <template v-else-if="currentRoute === 'rigging'">
            <HeroSection title-line-1="Такелажные работы" title-line-2="в" title-line-3="Москве"
                title-line-4="от 1000₽/час" title-line-5="Выполняем любые виды работ. Приедем за 60 минут"
                :hero-image-src="heroImage5" :show-br-desc="false" :show-br-mob="true"
                hero-image-alt="Такелажные работы" />
            <AdvantagesSection3 class="desktop-only" />
            <div class="main-content">
                <VideoPromoSection class="block-video" />
            </div>
            <PopularServices />
            <OnlineCalculator id="online-calculator" />
            <PhotoGallery />
            <ReviewsVideoSection />
            <GuaranteeSection2 class="block-guarantee" />
            <CallbackSection />
            <AdditionalServices />
            <RecommendationLetters />
            <FaqSection />
            <FinalCallbackSection />
            <ServicesTextSection2 />
        </template>

        <template v-else-if="currentRoute === 'transportation'">
            <HeroSection title-line-1="Грузоперевозки" title-line-2="в" title-line-3="Москве" title-line-4="от 249₽/час"
                :hero-image-src="heroImage6" hero-image-alt="Грузоперевозки" />
            <AdvantagesSection class="desktop-only" />
            <div class="main-content">
                <VideoPromoSection class="block-video" />
                <GuaranteeSection class="block-guarantee" />
            </div>
            <PopularServices />
            <OnlineCalculator id="online-calculator" />
            <PhotoGallery />
            <ReviewsVideoSection />
            <CallbackSection />
            <AdditionalServices />
            <RecommendationLetters />
            <FaqSection />
            <FinalCallbackSection />
            <ServicesTextSection />
        </template>

        <template v-else-if="currentRoute === 'handymen'">
            <HeroSection title-line-1="Услуги разнорабочих" title-line-2="в" title-line-3="Москве"
                title-line-4="от 249₽/час" :hero-image-src="heroImage8" hero-image-alt="Услуги разнорабочих" />
            <AdvantagesSection class="desktop-only" />
            <div class="main-content">
                <VideoPromoSection class="block-video" />
                <GuaranteeSection class="block-guarantee" />
            </div>
            <PopularServices />
            <OnlineCalculator id="online-calculator" />
            <PhotoGallery />
            <ReviewsVideoSection />
            <CallbackSection />
            <AdditionalServices />
            <RecommendationLetters />
            <FaqSection />
            <FinalCallbackSection />
            <ServicesTextSection />
        </template>

        <template v-else-if="currentRoute === 'legal'">
            <HeroSection title-line-1="Грузчики для юридических лиц" title-line-2="в" title-line-3="Москве"
                title-line-4="от 249₽/час" :hero-image-src="heroImage9" :show-br-desc="false" :show-br-mob="true"
                hero-image-alt="Грузчики для юридических лиц" />
            <AdvantagesSection class="desktop-only" />
            <div class="main-content">
                <VideoPromoSection class="block-video" />
                <GuaranteeSection class="block-guarantee" />
            </div>
            <PopularServices />
            <OnlineCalculator id="online-calculator" />
            <PhotoGallery />
            <ReviewsVideoSection />
            <CallbackSection />
            <AdditionalServices />
            <RecommendationLetters />
            <FaqSection />
            <FinalCallbackSection />
            <ServicesTextSection />
        </template>

        <BookmarkReminder />
        <SiteFooter />
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { onMounted, onUnmounted } from 'vue';

import heroImage from './public/warehouse_worker.jpg';
import heroImage2 from './public/loaders_hero.jpg';
import heroImage3 from './public/office_move_hero.jpg';
import heroImage4 from './public/movers_move_hero.jpg';
import heroImage5 from './public/rigging_hero.jpg';
import heroImage6 from './public/cargo_hero.jpg';
import heroImage7 from './public/oversized_cargo_hero.jpg';
import heroImage8 from './public/handymen_hero.jpg';
import heroImage9 from './public/legal_hero.jpg';

const currentRoute = ref('home');

const isArticleOpen = ref(false);
const currentPost = ref<any>(null);

const setRoute = (routeName: string) => {
    currentRoute.value = routeName;

    if (isArticleOpen.value) {
        isArticleOpen.value = false;
        currentPost.value = null;
    }

    window.scrollTo({ top: 0, behavior: 'smooth' });
};

const openArticle = (post: any) => {
    currentPost.value = post;
    isArticleOpen.value = true;
    window.scrollTo({ top: 0, behavior: 'smooth' });
};

const handleScrollToCalculator = (e: Event) => {
    const target = e.target as HTMLElement;
    if (target.closest('#scroll-to-calculator')) {
        e.preventDefault();
        const calculator = document.getElementById('online-calculator');
        if (calculator) {
            calculator.scrollIntoView({ behavior: 'smooth', block: 'start' });
        }
    }
};

onMounted(() => {
    document.addEventListener('click', handleScrollToCalculator);
});

onUnmounted(() => {
    document.removeEventListener('click', handleScrollToCalculator);
});
</script>

<style scoped lang="scss">
.desktop-only {
    display: block;
}

.main-content {
    display: flex;
    flex-direction: column;
    width: 100%;
}

@media (max-width: 1024px) {
    .desktop-only {
        display: none;
    }

    .block-guarantee {
        order: 1;
    }

    .block-video {
        order: 2;
    }
}
</style>