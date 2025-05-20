<template>
    <div class="footer">
        <div class="footer__logo">
            <img :src="clubInfo.logo" alt="Logo">
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
                        <span class="nav-text">About Us</span>
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
                    <span class="footer__content-title">Contact Information</span>
                    <div class="footer__content contact">
                        <div class="contact__details">
                            <i class="fa-solid fa-envelope"></i>
                            <span class="content__email">
                                {{ clubInfo.contactInfo.email }}
                            </span>
                        </div>
                        <div class="contact__details">
                            <i class="fa-solid fa-phone"></i>
                            <ul v-if="clubInfo.contactInfo.phoneInfo.length > 0" class="phone-list">
                                <li v-for="(info, i) in clubInfo.contactInfo.phoneInfo" :key="i" class="phone-info">
                                    <span class="phone-number">
                                        {{ info.number }}
                                    </span>
                                    <span class="phone-name">
                                        {{ info.nameandrole}}
                                    </span>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
        
                <div class="footer__item">
                    <span class="footer__content-title">Follow Us</span>
                    <div class="footer__content social-media">
                        <div class="social-media__content">
                            <a class="facebook" :href="clubInfo.socialMedia.facebook">
                                <i class="fa-brands fa-facebook-f fa-xl"></i>
                            </a>
                            <Tooltip
                            class="tooltip facebook"
                            :content="'Facebook'"
                            :trianglePositionWithContent="'down'"></Tooltip>
                        </div>
                        <div class="social-media__content">
                            <a class="instagram" :href="clubInfo.socialMedia.instagram">
                                <i class="fa-brands fa-instagram fa-xl"></i>
                            </a>
                            <Tooltip
                            class="tooltip instagram"
                            :content="'Instagram'"
                            :trianglePositionWithContent="'down'"></Tooltip>
                        </div>
                        <div class="social-media__content">
                            <a class="youtube" :href="clubInfo.socialMedia.youtube">
                                <i class="fa-brands fa-youtube fa-xl"></i>
                            </a>
                            <Tooltip
                            class="tooltip youtube"
                            :content="'Youtube'"
                            :trianglePositionWithContent="'down'"></Tooltip>
                        </div>
                        <div class="social-media__content">
                            <a class="tiktok" :href="clubInfo.socialMedia.tiktok">
                                <i class="fa-brands fa-tiktok fa-xl"></i>
                            </a>
                            <Tooltip
                            class="tooltip tiktok"
                            :content="'TikTok'"
                            :trianglePositionWithContent="'down'"></Tooltip>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Tooltip from '../common/Tooltip.vue';

export default {
    name: "Footer",
    components: {
        Tooltip
    },
    data() {
        return {
            clubInfo: {
                logo: require('@/assets/logo/logo.webp'),
                contactInfo: {
                    email: 'gdc.fpt2022@gmail.com',
                    phoneInfo: [
                        {
                            number: "0943551749",
                            nameandrole: "(Nguyen Thai Manh - President)"
                        },
                        {
                            number: "0705610637",
                            nameandrole: "(Tran Bich Ngoc - Vice President)"
                        }
                    ]
                },
                socialMedia: {
                    facebook: "https://www.facebook.com/gdcgwdance",
                    instagram: "https://www.instagram.com/gdc.gwhn/",
                    youtube: "https://www.youtube.com/@GDC-GreenwichDanceCrew",
                    tiktok: "https://www.tiktok.com/@greenwichdancecrew"
                }
            }
        }
    }
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
        font-family: Bebas Neue, sans-serif;
        font-size: 37px;
        font-weight: 600;

        @media screen and (max-width: 1440px) {
            font-size: 27px;
        }
    }

    .footer__content {
        display: flex;
        font-family: Poppins, sans-serif;

        &.navigation {
            flex-direction: column;
            text-decoration: none;
            text-align: left;
            font-size: 15px;
            padding: 0;
            gap: 0.75em;

            @media screen and (max-width: 360px) {
                font-size: 13.5px;
            }

            .navigation-items {
                display: flex;
                gap: 1em;
                margin: 0;
                padding: 0;
                color: $header-item-primary-color;
                text-decoration: none;

                & i {
                    margin-top: 0.15em;
                }
                
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
            font-size: 15px;
            gap: 0.5em;

            @media screen and (max-width: 360px) {
                font-size: 13.5px;
            }

            .contact__details {
                display: flex;
                gap: 1em;
                
                &:first-child {
                    align-items: center;
                }

                & i {
                    margin-top: 0.15em;
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

        }

        &.social-media {
            gap: 1.5em;

            .social-media__content {
                display: flex;
                position: relative;

                a {
                    padding: 0.25em 0.1em;
                    color: $header-item-primary-color;
                    transition: all 0.3s ease-in-out;
    
                    &:hover {
                        color: $header-item-secondary-color;
                    }

                    &.facebook, &.instagram, &.youtube, &.tiktok {
                        &:hover ~.tooltip{
                            opacity: 1;
                            transform: translateY(-10%);
                        }
                    }
                    
                    &:active {
                        color: $header-item-secondary-color;
                    }
                }
                
                & .tooltip {
                    opacity: 0;
                    position: absolute;
                    bottom: 120%;
                    z-index: 10;
                    transform: translateY(0);
                    transition: all 0.3s ease-in-out;
                    
                    &.facebook {
                        left: -165%;
                    }

                    &.instagram {
                        left: -115%;
                    }

                    &.youtube {
                        left: -65%;
                    }

                    &.tiktok {
                        left: -60%;
                    }
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
    padding: 1.5em 2em;
    background-color: $header-background-primary-color;

    @media screen and (max-width: 540px) {
        gap: 3em;
    }
    
    @media screen and (max-width: 360px) {
        gap: 1em;
    }

    .footer__logo {
        display: flex;
        align-items: center;
        
        img {
            width: 15.12em;
            height: 7em;

            @media screen and (max-width: 950px) {
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
        gap: 8.5em;

        @media screen and (max-width: 1440px) {
            gap: 4.5em;
        }

        @media screen and (max-width: 950px) {
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
            gap: 8.5em;

            .footer__item{
                @include footer-item();
            }

            @media screen and (max-width: 1440px) {
                gap: 4.5em;
            }

            @media screen and (max-width: 1024px) {
                flex-direction: column;
                gap: 2.75em;
            }
        }
    }
}
</style>