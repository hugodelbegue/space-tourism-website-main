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
.home_layout {
  display: flex;
  place-content: space-between;
  place-items: end;
  padding-top: calc(251px - 76px);
  padding-bottom: 131px;
  padding-right: 165px;
}

button {
  text-transform: uppercase;
}

h5 {
  color: var(--color-2);
}

.description {
  width: 450px;
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.button {
  width: 274px;
  height: 274px;

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

    &::before {
      z-index: -1;
      content: "";
      position: absolute;
      top: calc(50% - 450px /2);
      left: calc(50% - 450px /2);
      width: 450px;
      height: 450px;
      border-radius: 50%;
      transition: background .3s;
      opacity: 0;
    }

    &:hover {
      cursor: pointer;

      &::before {
        background: var(--color-3);
        opacity: .1;
      }
    }
  }
}
</style>