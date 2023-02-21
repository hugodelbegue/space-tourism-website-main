<script setup>
import Navbar from '@/components/Navbar.vue'
import NavMobile from '../components/NavMobile.vue'
</script>

<template>
    <header>
        <img alt="Space logo" class="logo" src="@/assets/shared/logo.svg" width="48" height="48" />
        <hr>
        <Navbar />
        <NavMobile />
    </header>
</template>

<style lang="scss" scoped>
@import '@/assets/scss/responsive.scss';

header {
    display: flex;
    place-content: space-between;
    place-items: center;
    padding-top: 40px;
    padding-left: 55px;
    padding-bottom: 76px;
    position: relative;

    @media #{$tabletLandscape} {
        padding-bottom: 40px;
        padding-left: 39px;
        padding-top: 40px;
    }

    @media #{$mobileMediumScreen} {
        padding-top: 30px;
        padding-bottom: 30px;
        padding-left: 24px;
    }

    @media #{$mobileDownScreen} {
        padding-bottom: 24px;
        padding-top: 24px;
    }
}

hr {
    z-index: 1;
    position: absolute;
    left: 167px;
    width: 473px;

    @media only screen and (max-width: 1360px) {
        width: 373px;
    }

    @media only screen and (max-width: 1280px) {
        width: 273px;
    }

    @media only screen and (max-width: 1180px) {
        width: 173px;
    }

    @media only screen and (max-width: 1080px) {
        width: 73px;
    }

    @media #{$tabletLandscape} {
        display: none;
    }
}

img {
    @media #{$mobileDownScreen} {
        width: 40px;
        height: 40px;
    }
}
</style>