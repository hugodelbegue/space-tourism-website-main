<script setup>
import { RouterView } from 'vue-router'
</script>

<template>
    <main>
        <RouterView />
    </main>
</template>

<style lang="scss" scoped>
@import '@/assets/scss/responsive.scss';

main {
    padding-left: 165px;

    @media #{$desktopMediumScreen} {
        padding-left: 100px;
    }

    @media #{$tabletLandscape} {
        padding-left: 59px;
        padding-right: 59px;
    }

    @media #{$tabletPortrait} {
        padding-left: 39px;
        padding-right: 39px;
    }

    @media #{$mobileDownScreen} {
        padding-left: 24px;
        padding-right: 24px;
    }
}
</style>