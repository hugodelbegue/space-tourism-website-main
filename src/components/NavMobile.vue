<script setup>
import { RouterLink } from 'vue-router'
</script>
<template>
    <nav class="nav_mobile">
        <input @change="toggleMenu" type="checkbox" id="burger">
        <label ref="cross" for="burger" class="burger" :class="classLink">
            <div ref="animation" class="iconMenu"></div>
        </label>
        <div ref="nav_links" class="nav_links">
            <RouterLink to="/" @click="toggleMenu"><span>00</span>Home</RouterLink>
            <RouterLink to="/destination" @click="toggleMenu"><span>01</span>Destination</RouterLink>
            <RouterLink to="/crew" @click="toggleMenu"><span>02</span>Crew</RouterLink>
            <RouterLink to="/technology" @click="toggleMenu"><span>03</span>Technology</RouterLink>
        </div>
    </nav>
</template>

<script>
export default {
    methods: {
        // Open and close links menu
        toggleMenu() {
            const { nav_links, animation, cross } = this.$refs;
            nav_links.classList.toggle('show');
            animation.classList.toggle('anim');
            cross.classList.toggle('elev');
            document.body.classList.toggle('hidden')
        }
    },
}
</script>
<style lang="scss" scoped>
@import '@/assets/scss/responsive.scss';

// nav mobile
nav {
    display: flex;
    place-items: center;

    @media #{$tabletLandscape} {
        padding: 0 24px !important;
    }
}

.nav_mobile {
    background: transparent;
    width: auto;
    z-index: 2;

    input[type="checkbox"] {
        display: none;
    }

    label {
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        width: 24px;
        height: 24px;
    }

    .iconMenu,
    .iconMenu::before,
    .iconMenu::after {
        content: "";
        background: currentColor;
        display: block;
        width: 24px;
        height: 3px;
        border-radius: 3px;
        position: relative;
        transition: transform .3s;
    }

    .iconMenu::before {
        top: 10px;
    }

    .iconMenu::after {
        bottom: 13px;
    }

    .nav_links {
        cursor: default;
        background: rgba(255, 255, 255, 0.04);
        backdrop-filter: blur(40px);
        position: absolute;
        top: 0;
        right: 0;
        display: none;
        flex-direction: column;
        place-items: left;
        gap: 20px;
        padding: 118px 0 377px 32px;
        width: 254px;
        height: 100vh;

        a {
            line-height: 19px;
            text-transform: uppercase;
            font-weight: 400;
            letter-spacing: 2.7px;
            border-right: 3px solid transparent;
            padding: 6px 0;

            &:active {
                mix-blend-mode: normal;
                border-right: 3px solid var(--color-3-hover);
            }
        }

        span {
            font-weight: 700;
            margin-right: 11px;
        }

        a.router-link-active {
            background: transparent;
            border-right: 3px solid var(--color-3);

        }
    }

    @media #{$tactilUpScreen} {
        display: none;
    }
}

.show {
    display: flex !important;

    @media #{$tactilUpScreen} {
        display: initial !important;
    }
}

.elev {
    position: fixed;
    z-index: 2;

    @media #{$tactilUpScreen} {
        position: static;
    }
}

a.elev {
    right: 1em;
    top: 1em;
}

label.elev {
    right: 24px;
    top: 34px;
}

.anim {
    transform: rotate(315deg);

    &.iconMenu::before {
        top: 0px !important;
        transform: rotate(0deg);
    }

    &.iconMenu::after {
        bottom: 3px !important;
        transform: rotate(-90deg);
    }
}
</style>