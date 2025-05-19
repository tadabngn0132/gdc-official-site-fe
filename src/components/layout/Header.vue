<template>
    <div class="header">
        <div class="header__logo">
            <router-link to="/">
                <img :src="clubInfo.logo" alt="Logo">
            </router-link>
        </div>

        <nav class="header__nav not-mobile">
            <router-link to="/" class="header__nav-items">
                <i class="fa-solid fa-house fa-lg"></i>
                <span class="nav-text">Home</span>
            </router-link>
            <router-link to="/#about" class="header__nav-items">
                <i class="fa-solid fa-circle-info fa-lg"></i>
                <span class="nav-text">About Us</span>
            </router-link>
            <router-link to="/#members" class="header__nav-items">
                <i class="fa-solid fa-users fa-lg"></i>
                <span class="nav-text">Members</span>
            </router-link>
            <router-link to="/#activities" class="header__nav-items">
                <i class="fa-solid fa-table-list fa-lg"></i>
                <span class="nav-text">Activities</span>
            </router-link>
            <router-link to="/#events" class="header__nav-items">
                <i class="fa-solid fa-calendar-day fa-lg"></i>
                <span class="nav-text">Events</span>
            </router-link>
        </nav>

        <div @click.stop="clickBarIcon" class="header__nav-bar-icon" :class="{ 'active': isHeaderNavOpen }">
            <i class="fa-solid fa-bars fa-2xl"></i>
        </div>

        <nav v-if="isHeaderNavOpen === true" @click.stop="closeHeaderNav" class="header__nav mobile">
            <router-link to="/" class="header__nav-items">
                <i class="fa-solid fa-house fa-lg"></i>
                <span class="nav-text">Home</span>
            </router-link>
            <router-link to="/#about" class="header__nav-items">
                <i class="fa-solid fa-circle-info fa-lg"></i>
                <span class="nav-text">About Us</span>
            </router-link>
            <router-link to="/#members" class="header__nav-items">
                <i class="fa-solid fa-users fa-lg"></i>
                <span class="nav-text">Members</span>
            </router-link>
            <router-link to="/#activities" class="header__nav-items">
                <i class="fa-solid fa-table-list fa-lg"></i>
                <span class="nav-text">Activities</span>
            </router-link>
            <router-link to="/#events" class="header__nav-items">
                <i class="fa-solid fa-calendar-day fa-lg"></i>
                <span class="nav-text">Events</span>
            </router-link>
        </nav>
    </div>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            clubInfo: {
                logo: require('@/assets/logo/logo.webp'),
            },
            isHeaderNavOpen: false
        }
    },
    methods: {
        clickBarIcon() {
            this.isHeaderNavOpen = !this.isHeaderNavOpen
        },
        closeHeaderNav() {
            this.isHeaderNavOpen = false
        }
    },
    mounted() {
        document.addEventListener('click', this.closeHeaderNav)
    },
    beforeDestroy() {
        document.removeEventListener('click', this.closeHeaderNav)
    }
}
</script>

<style scoped lang="scss">
$header-background-primary-color: #000;
$header-item-primary-color: #fff;
$header-item-secondary-color: #cb56b2;

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0.5em 1em;
    background-color: $header-background-primary-color;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 10000;

    .header__logo {
        display: flex;
        align-items: center;

        &:hover {
            opacity: 0.8;
        }

        &:active {
            opacity: 0.8;
        }
        
        img {
            width: 5.94em;
            height: 2.75em;
        }
    }
    
    .header__nav-bar-icon {
        display: none;
        color: $header-item-primary-color;
        padding: 0.25em;
        
        &.active {
            color: $header-item-secondary-color;
        }
        
        @media screen and (max-width: 450px) {
            display: inline;
        }

        i {
            color: inherit;
        }
    }
    
    .header__nav {
        display: flex;
        font-family: Poppins, sans-serif;
        background-color: $header-background-primary-color;
        text-align: left;
        padding: 0;

        &.mobile {
            display: none;
        }

        @media screen and (max-width: 450px) {
            flex-direction: column;
            position: absolute;
            top: 100%;
            left: 0;
            width: 100%;
            
            &.mobile {
                display: flex;
            }

            &.not-mobile {
                display: none;
            }
        }

        .header__nav-items {
            display: flex;
            align-items: center;
            gap: 1em;
            margin: 0;
            padding: 0.45em 1em;
            color: $header-item-primary-color;
            text-decoration: none;
            border-bottom: 0.15em solid $header-background-primary-color;

            &.router-link-exact-active {
                color: $header-item-secondary-color;
                border-bottom: 0.15em solid $header-item-secondary-color;
            }
            
            &:hover {
                color: $header-item-secondary-color;
                border-bottom: 0.15em solid $header-item-secondary-color;
            }

            &:active {
                color: $header-item-secondary-color;
                border-bottom: 0.15em solid $header-item-secondary-color;
            }

            @media screen and (max-width: 450px) {
                padding: 0.75em 1em;
            }

            i {
                display: none;

                @media screen and (max-width: 768px) {
                    display: inline;
                    padding: 0.65em 0;
                }

                @media screen and (max-width: 450px) {
                    font-size: 18px;
                    padding: 0;
                }
            }

            .nav-text {
                display: inline;
                
                @media screen and (max-width: 768px) {
                    display: none;
                }

                @media screen and (max-width: 450px) {
                    display: inline;
                    font-size: 18px;
                    margin-top: 0.175em;
                }
            }
        }
    }
}
</style>