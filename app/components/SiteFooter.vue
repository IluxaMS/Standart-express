<template>
    <footer class="site-footer">
        <div class="footer-container">
            <div class="footer-top">
                <div class="footer-logo">
                    <img src="../public/logo_placeholder_black.jpg" alt="Стандарт Экспресс" class="logo-img" />
                </div>

                <nav class="footer-nav">
                    <a href="#" class="nav-link">О компании</a>
                    <a href="#" class="nav-link">Вакансии</a>
                    <a href="#" class="nav-link">Новости</a>
                    <a href="#" class="nav-link">Контакты</a>
                </nav>

                <div class="footer-contacts">
                    <div class="contact-group">
                        <div class="contact-item phone-item">
                            <img src="../public/tel_icon.png" alt="phone" class="contact-icon" />
                            <div class="contact-info">
                                <div class="contact-links">
                                    <a href="tel:88007005153" class="contact-link main-phone">8 (800) 700-51-53</a>
                                    <div class="separator_mob">|</div>
                                    <a href="tel:+79652265790" class="contact-link sub-phone">+7 (965) 226-57-90</a>
                                </div>
                                <span class="contact-subtext">Принимаем звонки ежедневно<br>с 8:00 до 20:00 (по
                                    МСК)</span>
                            </div>
                        </div>
                    </div>

                    <div class="contact-group">
                        <div class="contact-item email-item">
                            <img src="../public/mail_icon.png" alt="email" class="contact-icon" />
                            <div class="contact-info">
                                <a href="mailto:info@standart-express.ru"
                                    class="contact-link email-link">info@standart-express.ru</a>
                                <span class="contact-subtext">Выполняем заказы: 24/7</span>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="footer-cta">
                    <button class="consult-btn">Заказать консультацию</button>
                </div>
            </div>

            <div class="footer-divider"></div>

            <div class="footer-bottom">
                <div class="legal-links legal-links_mob">
                    <a href="#" class="legal-link">Политика конфиденциальности</a>
                    <a href="#" class="legal-link">Пользовательское соглашение</a>
                </div>

                <div class="requisites requisites_mob">
                    ООО «Стандарт Экспресс»<br>
                    ОГРН 1141690046871<br>
                    ИНН 1657143487
                </div>

                <div class="copyright">
                    © 2024 Стандарт Экспресс. Все права защищены
                </div>

                <div class="legal-links legal-links_decs">
                    <a href="#" class="legal-link">Политика конфиденциальности</a>
                    <a href="#" class="legal-link">Пользовательское соглашение</a>
                </div>

                <div class="requisites requisites_decs">
                    ООО «Стандарт Экспресс»<br>
                    ОГРН 1141690046871<br>
                    ИНН 1657143487
                </div>
            </div>
        </div>
    </footer>
</template>

<style scoped lang="scss">
.site-footer {
    width: 100%;
    background-color: #1A1A1A;
    color: #FFFFFF;
    font-family: "Euclid Circular A", sans-serif;
    padding: 40px 0;
}

.footer-container {
    max-width: 1600px;
    margin: 0 auto;
    padding: 0 40px;
}

.footer-top {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 40px;
    margin-bottom: 25px;
}

.footer-logo {
    flex-shrink: 0;

    .logo-img {
        width: 146px;
        height: 35px;
        object-fit: contain;
        margin-bottom: 8px;
    }
}

.footer-nav {
    display: flex;
    gap: 18px;

    .nav-link {
        color: #FFFFFF;
        text-decoration: none;
        font-size: 14px;
        font-weight: 400;
        transition: color 0.2s;

        &:hover {
            color: #ED9121;
        }
    }
}

.footer-contacts {
    display: flex;
    gap: 40px;
}

.contact-group {
    display: flex;
    flex-direction: column;
}

.contact-item {
    display: flex;
    align-items: flex-start;
    gap: 10px;

    .contact-icon {
        width: 20px;
        height: 20px;
        object-fit: contain;
        margin-top: 2px;
    }
}

.contact-info,
.contact-links {
    display: flex;
    flex-direction: column;
}

.contact-link {
    color: #FFFFFF;
    text-decoration: none;
    font-size: 14px;
    font-weight: 400;
    line-height: 1.4;
    transition: color 0.2s;

    &:hover {
        color: #ED9121;
    }
}

.main-phone {
    font-size: 16px;
    padding-left: 10px;
}

.sub-phone {
    font-size: 14px;
    font-weight: 300;
}

.email-link {
    font-size: 14px;
}

.contact-subtext {
    font-size: 12px;
    font-weight: 300;
    line-height: 1.4;
    margin-top: 4px;
}

.footer-cta {
    flex-shrink: 0;
}

.consult-btn {
    width: 200px;
    height: 50px;
    border-radius: 100px;
    background-color: #ED9121;
    border: none;
    color: #FFFFFF;
    font-family: "Euclid Circular A", sans-serif;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    transition: filter 0.2s;
    margin-bottom: 20px;

    &:hover {
        filter: brightness(1.1);
    }
}

.footer-divider {
    width: 82%;
    height: 1px;
    background-color: rgba(255, 255, 255, 0.1);
    margin-bottom: 30px;
    margin-left: 140px;
}

.footer-bottom {
    display: flex;
    align-items: flex-start;
    justify-content: space-around;
    gap: 40px;
    margin-left: 103px;
    margin-right: 90px;
}

.copyright {
    font-size: 14px;
    font-weight: 300;
    color: rgba(255, 255, 255, 0.7);
    max-width: 348px;
}

.legal-links {
    display: flex;
    gap: 30px;

    .legal-link {
        font-size: 14px;
        font-weight: 300;
        color: rgba(255, 255, 255, 0.7);
        text-decoration: underline;
        text-decoration-style: solid;
        transition: color 0.2s;
        margin-right: 10px;

        &:hover {
            color: #ED9121;
        }
    }
}

.requisites {
    font-size: 13px;
    font-weight: 400;
    color: rgba(255, 255, 255, 0.7);
    line-height: 1.6;
    text-align: left;
    max-width: 176px;
    margin-right: 40px;
}

.separator_mob {
    display: none;
}

.legal-links_mob,
.requisites_mob {
    display: none;
}

@media (max-width: 1200px) {
    .footer-top {
        flex-wrap: wrap;
        gap: 30px;
    }

    .footer-contacts {
        width: 100%;
        justify-content: space-between;
    }

    .footer-bottom {
        flex-wrap: wrap;
        gap: 20px;
    }

    .requisites {
        text-align: left;
        width: 100%;
    }
}

@media (max-width: 768px) {
    .footer-logo {
        margin-left: 30%;
    }

    .site-footer {
        padding: 30px 0;
    }

    .footer-container {
        padding: 0 20px;
    }

    .footer-top {
        flex-direction: column;
        align-items: flex-start;
    }

    .footer-nav {
        flex-wrap: wrap;
        gap: 19px;
    }

    .separator_mob {
        margin: 0 10px;
        display: block;
        font-weight: 300;
        font-size: 16px;
        color: #7D7D7D;
    }

    .main-phone {
        padding: 0;
    }

    .contact-icon {
        margin-right: 5px;
        margin-left: -2px;
    }

    .consult-btn {
        width: 330px;
        margin-bottom: 7px;
    }

    .footer-divider {
        margin-left: -20px;
        width: 111%;
    }

    .contact-links {
        flex-direction: row;
    }

    .footer-contacts {
        flex-direction: column;
        gap: 20px;
    }

    .footer-bottom {
        flex-direction: row;
        gap: 20px;
        margin: 0;
    }

    .legal-links {
        flex-direction: row;
        gap: 10px;
    }

    .legal-links_mob,
    .requisites_mob {
        display: flex;
        gap: 50px;

        br {
            display: none;
        }
    }

    .legal-links_decs,
    .requisites_decs {
        display: none;
    }

    .copyright,
    .legal-links,
    .requisites {
        max-width: 100%;
        margin: 0;
    }
}
</style>