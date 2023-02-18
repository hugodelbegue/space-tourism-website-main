<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
    <nav>
        <RouterLink to="/"><span>00</span>Home</RouterLink>
        <RouterLink to="/destination"><span>01</span>Destination</RouterLink>
        <RouterLink to="/crew"><span>02</span>Crew</RouterLink>
        <RouterLink to="/technology"><span>03</span>Technology</RouterLink>
    </nav>
</template>

<style lang="scss" scoped>
@import '@/assets/scss/responsive.scss';

nav {
    display: flex;
    place-content: space-between;
    place-items: center;
    width: 830px;
    height: 96px;
    padding: 39px 165px 35px 123px;
    background: rgba(255, 255, 255, 0.04);
    backdrop-filter: blur(40.7742px);
    line-height: 89px;

    @media #{$tabletLandscape} {
        width: 600px;
        padding: 40px 48px;
    }

    @media #{$tabletPortrait} {
        width: 450px;
    }

    a {
        text-transform: uppercase;
        font-weight: 400;
        letter-spacing: 2.7px;
        border-bottom: 3px solid transparent;
        transition: .4s;

        &:hover {
            mix-blend-mode: normal;
            border-bottom: 3px solid var(--color-3-hover);
        }

        @media #{$tabletPortrait} {
            font-size: 14px;
            line-height: 92px;
        }
    }

    span {
        font-weight: 700;
        margin-right: 11px;

        @media #{$tabletPortrait} {
            display: none;
        }
    }
}

.router-link-active {
    border-bottom: 3px solid var(--color-3);
}
</style>