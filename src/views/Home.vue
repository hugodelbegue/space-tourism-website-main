<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
  <div class="home">
    <div class="home_layout">
      <div class="description">
        <h5>So, you want to travel to</h5>
        <h1>Space</h1>
        <p>Let’s face it; if you want to go to space, you might as well genuinely go to
          outer space and not hover kind of on the edge of it. Well sit back, and
          relax because we’ll give you a truly out of this world experience!</p>
      </div>
      <div class="button">
        <RouterLink to="/destination"><button>Explore</button></RouterLink>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import '@/assets/scss/responsive.scss';

.home_layout {
  display: flex;
  place-content: space-between;
  place-items: end;
  padding-top: calc(251px - 76px);
  padding-bottom: 131px;
  padding-right: 165px;

  @media #{$desktopMediumScreen} {
    padding-left: 41px;
    padding-right: 100px;
  }

  @media #{$desktopDownScreen} {
    padding-left: 0;
    padding-top: 66px;
  }

  @media #{$tabletLandscape} {
    padding-right: 0;
    place-items: center;
  }

  @media #{$tabletPortrait} {
    flex-direction: column;
    place-items: center;
  }

  @media #{$mobileMediumScreen} {
    padding-top: 25px;
  }

  @media #{$mobileDownScreen} {
    padding-top: 0;
  }
}

h1 {
  @media #{$tabletMedium} {
    font-size: 125px;
  }

  @media #{$tabletPortrait} {
    line-height: 150px;
    font-size: 150px;
  }

  @media #{$mobileMediumScreen} {
    font-size: 110px;
    line-height: 120px;
  }

  @media #{$mobileDownScreen} {
    font-size: 80px;
    line-height: 100px;
  }
}

h5 {
  color: var(--color-2);

  @media #{$mobileDownScreen} {
    margin-bottom: 0 !important;
  }
}

.description {
  width: 450px;
  display: flex;
  flex-direction: column;
  gap: 24px;

  @media #{$tabletMedium} {
    width: 350px;
  }

  @media #{$tabletPortrait} {
    width: 450px;
    place-items: center;
    text-align: center;
    margin-bottom: 156px;
  }

  @media #{$mobileMediumScreen} {
    width: 350px;
    margin-top: 0;
    margin-bottom: 81px;
  }

  @media #{$mobileDownScreen} {
    width: 327px;
    gap: 16px;
  }
}

.button {
  width: 274px;
  height: auto;
  aspect-ratio: 1/1;

  @media #{$tabletLandscape} {
    width: 258px;
  }

  @media #{$tabletPortrait} {
    width: 242px;
  }

  @media #{$mobileMediumScreen} {
    width: 200px;
  }

  @media #{$mobileDownScreen} {
    width: 150px;
  }

  button {
    z-index: 0;
    width: 100%;
    height: 100%;
    border-radius: 50%;
    font-family: var(--font-family-heading);
    font-style: normal;
    font-weight: 400;
    font-size: 32px;
    line-height: 37px;
    letter-spacing: 2px;
    color: var(--color-1);
    border-color: var(--color-3);
    text-transform: uppercase;

    @media #{$mobileDownScreen} {
      font-size: 20px;
      line-height: 23px;
      letter-spacing: 1.25px;
    }

    &::before {
      z-index: -1;
      content: "";
      position: absolute;
      top: calc(50% - 450px /2);
      left: calc(50% - 450px /2);
      width: 450px;
      height: auto;
      aspect-ratio: 1/1;
      border-radius: 50%;
      transition: background .3s;
      opacity: 0;
      border-color: var(--color-3);

      @media #{$tabletLandscape} {
        width: 350px;
        top: calc(50% - 350px /2);
        left: calc(50% - 350px /2);
      }

      @media #{$mobileMediumScreen} {
        width: 250px;
        top: calc(50% - 250px /2);
        left: calc(50% - 250px /2);
      }

      @media #{$mobileDownScreen} {
        width: 200px;
        top: calc(50% - 200px /2);
        left: calc(50% - 200px /2);
      }
    }

    &:active {
      &::before {
        background: var(--color-3);
        opacity: .1;
      }
    }

    @media #{$tactilUpScreen} {
      &:hover {
        cursor: pointer;

        &::before {
          background: var(--color-3);
          opacity: .1;
        }
      }
    }
  }
}
</style>