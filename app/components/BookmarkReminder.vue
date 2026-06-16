<template>
    <section class="bookmark-section">
        <img src="../public/bg-pattern2.png" alt="" class="bg-pattern" />
        <img src="../public/decor_line_left.png" alt="" class="decor-left" />
        <img src="../public/decor_line_right.png" alt="" class="decor-right" />
        <div class="bookmark-container">
            <h2 class="bookmark-title">
                Чтобы не потерять наш сайт добавьте его<br />
                в избранное (закладки) или сохраните
            </h2>
            <div class="action-block">
                <p class="instruction-text">Нажмите сочетание<br />клавиш в браузере</p>
                <div class="key-button">
                    Ctrl + D
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped lang="scss">
.bookmark-section {
    position: relative;
    width: 100%;
    min-height: 370px;
    background-color: #1A1A1A;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    font-family: "Euclid Circular A", sans-serif;
}

.bg-pattern {
    position: absolute;
    top: 0;
    left: -33px;
    width: 102%;
    height: 100%;
    object-fit: cover;
    pointer-events: none;
    z-index: 0;
}

.decor-left {
    position: absolute;
    left: 0%;
    bottom: 40px;
    width: 221px;
    height: 59px;
    pointer-events: none;
    z-index: 1;
}

.decor-right {
    position: absolute;
    right: 0%;
    top: 40px;
    width: 221px;
    height: 59px;
    pointer-events: none;
    z-index: 1;
}

.bookmark-container {
    position: relative;
    z-index: 2;
    width: 100%;
    max-width: 1600px;
    padding: 0 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
}

.bookmark-title {
    font-weight: 700;
    font-size: 32px;
    line-height: 100%;
    color: #FFFFFF;
    margin: 0 0 40px 0;
    white-space: pre-line;
}

.action-block {
    display: flex;
    align-items: center;
    gap: 40px;
}

.instruction-text {
    font-weight: 300;
    font-size: 24px;
    line-height: 120%;
    color: #FFFFFF;
    margin: 0;
    text-align: left;
    white-space: pre-line;
}

.key-button {
    width: 258px;
    height: 95px;
    background-color: #FFFFFF;
    border-radius: 20px;
    display: flex;
    align-items: center;
    justify-content: center;

    font-weight: 700;
    font-size: 36px;
    color: #000000;
    transition: transform 0.1s, box-shadow 0.1s;
    cursor: pointer;
}

@media (max-width: 768px) {
    .bookmark-section {
        display: none;
    }
}
</style>