<script setup>
import Destination from '@/assets/data/data.json'
</script>

<template>
    <div class="destination">
        <div class="destination_layout">
            <h5><span>01</span>Pick your destination</h5>
            <div class="content" v-for="data in Destination.destinations">
                <div class="destination_container" v-if="data.name == this.name">
                    <div class="picture_container appearance" v-if="data.images['webp']">
                        <img :src="imgUrl(data.images['webp'])" :alt="data.name + ' planet image'">
                    </div>
                    <div class="description">
                        <div class="planet_nav">
                            <ul>
                                <li @click="page('Moon')" :class="moon">Moon</li>
                                <li @click="page('Mars')" :class="mars">Mars</li>
                                <li @click="page('Europa')" :class="europa">Europa</li>
                                <li @click="page('Titan')" :class="titan">Titan</li>
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
        page(name) {
            if (name == Destination['destinations'][0].name) {
                return this.name = 'Moon';
            } else if (name == Destination['destinations'][1].name) {
                return this.name = 'Mars';
            } else if (name == Destination['destinations'][2].name) {
                return this.name = 'Europa';
            } else if (name == Destination['destinations'][3].name) {
                return this.name = 'Titan';
            }
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
.destination_layout {
    padding-bottom: 118px;
    padding-right: 165px;

    h2 {
        margin: 37px 0 14px;
    }

    h5 {
        margin-bottom: 64px;
    }
}

.destination_container {
    display: flex;
    place-items: end;
    place-content: space-between;
    margin-left: calc(230px - 166.5px);
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
            height: 100%;
            color: var(--color-2);
            border-bottom: 3px solid transparent;
            text-transform: uppercase;
            letter-spacing: 2.7px;
            transition: .4s;

            &:hover {
                cursor: pointer;
                border-bottom: 3px solid var(--color-3-hover);
            }

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
        letter-spacing: 2.3625px;
        text-transform: uppercase;
        margin-bottom: 12px;
    }

    .number {
        font-family: var(--font-family-heading);
        line-height: 32px;
        text-transform: uppercase;
        font-size: 28px;
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