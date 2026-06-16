<template>
    <section class="downloads-section">
        <img src="../public/decor_left.png" alt="" class="decor decor--top-left" />
        <img src="../public/decor_right.png" alt="" class="decor decor--bottom-right" />
        <img src="../public/icon_cubes.png" alt="" class="cubes-icon" />

        <div class="downloads-container">
            <h2 class="downloads-title">МАТЕРИАЛЫ ДЛЯ СКАЧИВАНИЯ</h2>

            <div class="logos-grid">
                <div class="logo-item">
                    <img src="../public/logo_preview_1.png" alt="Логотип 1" class="logo-preview" />
                </div>
                <div class="logo-item">
                    <img src="../public/logo_preview_2.png" alt="Логотип 2" class="logo-preview" />
                </div>
                <div class="logo-item">
                    <img src="../public/logo_preview_3.png" alt="Логотип 3" class="logo-preview" />
                </div>
                <div class="logo-item">
                    <img src="../public/logo_preview_4.png" alt="Логотип 4" class="logo-preview" />
                </div>
            </div>

            <div class="download-links">
                <a href="#" class="download-link">
                    Логотип в формате <span>(pdf)</span>
                </a>
                <a href="#" class="download-link">
                    Логотип в векторных форматах <span>(ai, cdr, eps)</span>
                </a>
                <a href="#" class="download-link">
                    Логотип в растровых форматах <span>(jpg, png, psd)</span>
                </a>
            </div>
        </div>
    </section>
</template>

<style scoped lang="scss">
.downloads-section {
    position: relative;
    width: 100%;
    height: 527px;
    background-color: #FFFFFF;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 10px 0 30px 0;
}

.downloads-container {
    position: relative;
    z-index: 2;
    max-width: 1600px;
    width: 100%;
    margin: 0 auto;
    padding: 0 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.downloads-title {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 700;
    font-size: 42px;
    line-height: 100%;
    color: #000;
    text-transform: uppercase;
    margin: 70px 0 90px 0;
    letter-spacing: 0%;
    text-align: center;
}

.logos-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 30px;
    width: 100%;
    max-width: 1200px;
    margin-bottom: 50px;
}

.logo-item {
    display: flex;
    justify-content: center;
    align-items: center;
}

.logo-preview {
    width: 260px;
    height: 159px;
    object-fit: contain;
}

.download-links {
    display: flex;
    flex-direction: column;
    gap: 15px;
    align-items: flex-start;
    width: 100%;
    max-width: 1180px;
}

.download-link {
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 100%;
    color: #000;
    text-decoration: none;
    transition: color 0.2s;

    &:hover {
        color: #ED9121;

        span {
            color: #ED9121;
        }
    }

    span {
        color: #ED9121;
        font-weight: 400;
        font-size: 16px;
    }
}

.decor {
    position: absolute;
    z-index: 1;
    pointer-events: none;
}

.decor--bottom-right {
    top: 60px;
    right: 0;
    width: 220px;
}

.decor--top-left {
    bottom: 40px;
    left: 0;
    width: 150px;
}

.cubes-icon {
    position: absolute;
    bottom: 40px;
    right: 40px;
    width: 90px;
    height: 85px;
    z-index: 1;
    object-fit: contain;
}

@media (max-width: 1024px) {
    .downloads-section {
        height: auto;
        min-height: 1220px;
        padding: 0 0 20px 0;
    }

    .downloads-container {
        padding: 0 20px;
        align-items: center;
    }

    .downloads-title {
        font-size: 32px;
        margin: 0;
        margin-bottom: 40px;
        text-align: center;
    }

    .logos-grid {
        grid-template-columns: 1fr;
        gap: 30px;
        max-width: 378px;
        margin-bottom: 40px;
    }

    .logo-preview {
        width: 100%;
        max-width: 343px;
        height: auto;
        aspect-ratio: 260 / 159;
    }

    .download-links {
        align-items: flex-start;
        max-width: 100%;
        gap: 20px;
    }

    .download-link {
        font-size: 16px;
        text-align: left;
    }

    .decor,
    .cubes-icon {
        display: none;
    }
}
</style>