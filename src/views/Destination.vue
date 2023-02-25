<script setup>
import Destination from '@/assets/data/data.json'
import { ref } from 'vue'

const planetName = ref('Moon');
function page(name) {
    for (const destination of Destination['destinations']) {
        if (name === destination.name) {
            planetName.value = destination.name;
            break;
        }
    }
}
</script>

<template>
    <div class="destination">
        <div class="destination_layout">
            <h5><span>01</span>Pick your destination</h5>
            <div class="content" v-for="data in Destination.destinations">
                <div class="destination_container" v-if="data.name == planetName">
                    <div class="picture_container appearance" v-if="data.images['webp']">
                        <img :src="imgUrl(data.images['webp'])" :alt="data.name + ' planet image'">
                    </div>
                    <div class="description">
                        <div class="planet_nav">
                            <ul>
                                <li @click="page('Moon'), underline('Moon')" :class="moon">Moon</li>
                                <li @click="page('Mars'), underline('Mars')" :class="mars">Mars</li>
                                <li @click="page('Europa'), underline('Europa')" :class="europa">Europa</li>
                                <li @click="page('Titan'), underline('Titan')" :class="titan">Titan</li>
                            </ul>
                        </div>
                        <h2 class="offsetX" v-if="data.name">{{ data.name }}</h2>
                        <p class="offsetX" v-if="data.description">{{ data.description }}</p>
                        <hr>
                        <div class="statistics offsetY" v-if="data.distance && data.travel">
                            <div class="distance">
                                <div class="indicative">Avg. distance</div>
                                <span class="number">{{ data.distance }}</span>
                            </div>
                            <div class="time">
                                <div class="indicative">Est. travel time</div>
                                <span class="number">{{ data.travel }}</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: 'Moon',
            imgUrl(file) {
                return new URL(`../assets/img/destination/${file}`, import.meta.url).href;
            }
        }
    },
    methods: {
        underline(name) {
            const destinations = Destination['destinations'];
            const names = destinations.map(destination => destination.name);
            const index = names.indexOf(name);

            if (index >= 0) {
                const planet = destinations[index].name;
                this.name = planet;
                return planet;
            }
            return null;
        }
    },
    computed: {
        moon() {
            return {
                focus: this.name == 'Moon'
            }
        },
        mars() {
            return {
                focus: this.name == 'Mars'
            }
        },
        europa() {
            return {
                focus: this.name == 'Europa'
            }
        },
        titan() {
            return {
                focus: this.name == 'Titan'
            }
        }
    }
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/responsive.scss';

.destination_layout {
    padding-bottom: 118px;
    padding-right: 165px;

    h2 {
        margin: 37px 0 14px;

        @media #{$tabletPortrait} {
            margin: 32px 0 8px;
        }

        @media #{$mobileDownScreen} {
            font-size: 56px;
            line-height: 64px;
            margin: 20px 0 1px;
        }
    }

    h5 {
        margin-bottom: 64px;
    }

    @media #{$desktopMediumScreen} {
        padding-right: 100px;
    }

    @media #{$tabletLandscape} {
        padding-bottom: 0;
        padding-right: 0;
    }
}

.destination_container {
    display: flex;
    place-items: center;
    place-content: space-between;
    margin-left: calc(230px - 166.5px);

    @media #{$desktopDownScreen} {
        margin-left: 0;
    }

    @media #{$tabletPortrait} {
        text-align: center;
        flex-direction: column;
    }
}

img {
    width: 445px;
    height: auto;
    aspect-ratio: 1/1;

    @media #{$desktopMediumScreen} {
        width: 350px;
    }

    @media #{$tabletLandscape} {
        width: 325px;
    }

    @media #{$tabletMedium} {
        width: 300px;
    }

    @media #{$mobileMediumScreen} {
        width: 250px;
    }

    @media #{$mobileDownScreen} {
        width: 170px;
    }
}

.description {
    width: 445px;
    height: 472px;
    display: flex;
    flex-direction: column;

    hr {
        margin: 54px 0 28px;
        background: #383b4b;
        border: 1px solid #383b4b;

        @media #{$tabletPortrait} {
            margin: 49px 0 28px;
            width: 100%;
        }

        @media #{$mobileDownScreen} {
            margin: 32px 0;
            width: 327px;
        }
    }

    @media #{$tabletMedium} {
        width: 315px;
    }

    @media #{$tabletPortrait} {
        place-items: center;
        width: 576px;
    }

    @media #{$mobileUpScreen} {
        width: 400px;
    }

    @media #{$mobileMediumScreen} {
        width: 350px;
    }
}

.planet_nav {
    ul {
        height: 34px;
        display: flex;
        place-items: flex-start;
        gap: 36px;
        padding-left: 0;

        li {
            cursor: pointer;
            height: 100%;
            color: var(--color-2);
            border-bottom: 3px solid transparent;
            text-transform: uppercase;
            letter-spacing: 2.7px;
            font-size: 16px;
            line-height: 19px;
            transition: .4s;

            &:active {
                border-bottom: 3px solid var(--color-3-hover);
            }

            @media #{$tactilUpScreen} {
                &:hover {
                    border-bottom: 3px solid var(--color-3-hover);
                }
            }

            @media #{$mobileDownScreen} {
                font-size: 14px;
                line-height: 17px;
                letter-spacing: 2.35px;
            }
        }

        @media #{$tabletPortrait} {
            margin-top: 53px;
        }

        @media #{$mobileDownScreen} {
            margin-top: 26px;
        }
    }
}

.focus {
    color: var(--color-3) !important;
    border-bottom: 3px solid var(--color-3) !important;
}

.statistics {
    display: flex;
    gap: 79px;

    .indicative {
        color: var(--color-2);
        font-size: 14px;
        line-height: 17px;
        letter-spacing: 2.35px;
        text-transform: uppercase;
        margin-bottom: 12px;
    }

    .number {
        font-family: var(--font-family-heading);
        line-height: 32px;
        text-transform: uppercase;
        font-size: 28px;
    }

    @media #{$mobileDownScreen} {
        flex-direction: column;
        gap: 32px;
    }
}

// transitions

.appearance {
    animation: appearance 1.5s ease;
}

.offsetX {
    animation: offsetX .7s ease;
}

.offsetY {
    animation: offsetY .7s ease;
}

@keyframes appearance {
    from {
        opacity: 0;
    }

    to {
        opacity: 1;
    }
}

@keyframes offsetX {
    from {
        transform: translateX(50px);
    }

    to {
        transform: translateX(0px);
    }
}

@keyframes offsetY {
    from {
        transform: translateY(25px);
    }

    to {
        transform: translateY(0px);
    }
}
</style>