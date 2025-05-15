<template>
    <div class="footer">
        <div class="footer__logo">
            <img src="@/assets/logo/logo.webp" alt="Logo">
        </div>

        <div class="footer__items">
            <nav class="footer__item">
                <span class="footer__content-title">Site Navigation</span>
                <div class="footer__content navigation">
                    <router-link to="/" class="navigation-items">
                        <i class="fa-solid fa-house"></i>
                        <span class="nav-text">Home</span>
                    </router-link>
                    <router-link to="/#about" class="navigation-items">
                        <i class="fa-solid fa-circle-info"></i>
                        <span class="nav-text">About</span>
                    </router-link>
                    <router-link to="/#members" class="navigation-items">
                        <i class="fa-solid fa-users"></i>
                        <span class="nav-text">Members</span>
                    </router-link>
                    <router-link to="/#activities" class="navigation-items">
                        <i class="fa-solid fa-table-list"></i>
                        <span class="nav-text">Activities</span>
                    </router-link>
                    <router-link to="/#events" class="navigation-items">
                        <i class="fa-solid fa-calendar-day"></i>
                        <span class="nav-text">Events</span>
                    </router-link>
                </div>
            </nav>

            <div class="footer__items-last">
                <div class="footer__item">
                    <span class="footer__content-title">Contact information</span>
                    <div class="footer__content contact">
                        <div class="contact__details">
                            <i class="fa-solid fa-envelope"></i>
                            <span class="content__email">gdc.fpt2022@gmail.com</span>
                        </div>
                        <div class="contact__details">
                            <i class="fa-solid fa-phone"></i>
                            <div class="phone-list">
                                <div class="phone-info">
                                    <span class="phone-number">0943551749</span>
                                    <span class="phone-name">(Nguyễn Thái Mạnh - President)</span>
                                </div>
                                <div class="phone-info">
                                    <span class="phone-number">0705610637</span>
                                    <span class="phone-name">(Trần Bích Ngọc - Vice President)</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
        
                <div class="footer__item">
                    <span class="footer__content-title">Follow us</span>
                    <div class="footer__content social-media">
                        <a href="https://www.facebook.com/gdcgwdance">
                            <i class="fa-brands fa-facebook-f fa-xl"></i>
                        </a>
                        <a href="https://www.instagram.com/gdc.gwhn/">
                            <i class="fa-brands fa-instagram fa-xl"></i>
                        </a>
                        <a href="https://www.youtube.com/@GDC-GreenwichDanceCrew">
                            <i class="fa-brands fa-youtube fa-xl"></i>
                        </a>
                        <a href="https://www.tiktok.com/@greenwichdancecrew">
                            <i class="fa-brands fa-tiktok fa-xl"></i>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Footer"
}
</script>

<style scoped lang="scss">
$header-background-primary-color: #000;
$header-item-primary-color: #fff;
$header-item-secondary-color: #cb56b2;

@mixin footer-item {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 1em;
    color: $header-item-primary-color;

    .footer__content-title {
        font-size: 18px;
        font-weight: 600;
    }

    .footer__content {
        display: flex;

        &.navigation {
            flex-direction: column;
            text-decoration: none;
            font-weight: 500;
            text-align: left;
            padding: 0;
            gap: 0.75em;

            .navigation-items {
                display: flex;
                gap: 1em;
                margin: 0;
                padding: 0;
                color: $header-item-primary-color;
                text-decoration: none;
                font-weight: 500;
                
                &:hover {
                    color: $header-item-secondary-color;
                }

                &:active {
                    color: $header-item-secondary-color;
                }
            }
        }

        &.contact {
            flex-direction: column;
            gap: 0.5em;

            .contact__details {
                display: flex;
                gap: 1em;
            }

            .phone-list {
                display: flex;
                flex-direction: column;
                align-items: flex-start;
                text-align: left;
                gap: 0.25em;

                .phone-info {
                    display: flex;
                    gap: 0.15em;

                    @media screen and (max-width: 768px) {
                        flex-direction: column;
                        gap: 0.75em;
                    }
                }
            }
        }

        &.social-media {
            gap: 1.5em;

            a {
                padding: 0.25em 0.1em;
                color: $header-item-primary-color;

                &:hover {
                    color: $header-item-secondary-color;
                }

                &:active {
                    color: $header-item-secondary-color;
                }
            }
        }
    }
}

* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}

.footer {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    padding: 1.5em 1em;
    background-color: $header-background-primary-color;
    position: fixed;
    bottom: 0;
    width: 100%;

    @media screen and (max-width: 540px) {
        gap: 3em;
    }

    .footer__logo {
        display: flex;
        align-items: center;
        
        img {
            width: 12.96em;
            height: 6em;

            @media screen and (max-width: 768px) {
                width: 10.8em;
                height: 5em;
            }

            @media screen and (max-width: 540px) {
                width: 6.48em;
                height: 3em;
            }
        }
    }

    .footer__items {
        display: flex;
        gap: 5.75em;

        @media screen and (max-width: 768px) {
            gap: 4em;
        }

        @media screen and (max-width: 540px) {
            flex-direction: column;
            gap: 2.75em;
        }

        .footer__item {
            @include footer-item();
        }

        .footer__items-last {
            display: flex;
            gap: 5.75em;

            .footer__item{
                @include footer-item();
            }

            @media screen and (max-width: 1024px) {
                flex-direction: column;
                gap: 2.75em;
            }
        }
    }
}
</style>