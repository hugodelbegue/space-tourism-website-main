<script setup>
import Header from '@/layouts/Header.vue'
import Main from '@/layouts/Main.vue'
</script>

<template>
  <div class="app_layout" :class="background">
    <Header />
    <Main />
  </div>
</template>

<script>
export default {
  computed: {
    background() {
      return {
        home: this.$route.name == 'Home',
        destination: this.$route.name == 'Destination',
        crew: this.$route.name == 'Crew',
        technology: this.$route.name == 'Technology'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/responsive.scss';

.app_layout {
  // height: 100vh;
  width: 100%;
  background-repeat: no-repeat;
  background-size: cover;

  @media #{$tabletPortrait} {
    overflow-y: hidden;
  }
}

.home {
  background-image: url(@/assets/img/home/background-home-desktop.jpg);

  @media #{$tabletPortrait} {
    background-image: url(@/assets/img/home/background-home-tablet.jpg);
  }
}

.destination {
  background-image: url(@/assets/img/destination/background-destination-desktop.jpg);

  @media #{$tabletPortrait} {
    background-image: url(@/assets/img/destination/background-destination-tablet.jpg);
  }
}

.crew {
  background-image: url(@/assets/img/crew/background-crew-desktop.jpg);

  @media #{$tabletPortrait} {
    background-image: url(@/assets/img/crew/background-crew-tablet.jpg);
  }
}

.technology {
  background-image: url(@/assets/img/technology/background-technology-desktop.jpg);

  @media #{$tabletPortrait} {
    background-image: url(@/assets/img/technology/background-technology-tablet.jpg);
  }
}
</style>
