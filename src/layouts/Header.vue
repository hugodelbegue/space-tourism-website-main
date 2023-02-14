<script setup>
import Navbar from '@/components/Navbar.vue'
</script>

<template>
    <header>
        <img alt="Space logo" class="logo" src="@/assets/shared/logo.svg" width="48" height="48" />
        <hr>
        <Navbar />
    </header>
</template>

<style lang="scss" scoped>
header {
    display: flex;
    place-content: space-between;
    place-items: center;
    // max-width: 1385px;
    padding-top: 40px;
    padding-left: 55px;
}

hr {
    z-index: 1;
    position: absolute;
    left: 167px;
    width: 473px;
}
</style>