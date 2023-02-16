<script setup>
import Crew from '@/assets/data/data.json'
</script>

<template>
    <div class="crew">
        <div class="crew_layout">
            <div class="content" v-for="data in Crew.crew">
                <div class="description" v-if="data.name == this.name">
                    <h5><span>02</span>Meet your crew</h5>
                    <h4 v-if="data.role" class="offsetX">{{ data.role }}</h4>
                    <h3 v-if="data.name" class="offsetX">{{ data.name }}</h3>
                    <p v-if="data.bio" class="offsetX">{{ data.bio }}</p>
                    <div class="bullet_list">
                        <span @click="page('Douglas Hurley')" :class="bulletOne"></span>
                        <span @click="page('Mark Shuttleworth')" :class="bulletTwo"></span>
                        <span @click="page('Victor Glover')" :class="bulletThree"></span>
                        <span @click="page('Anousheh Ansari')" :class="bulletFour"></span>
                    </div>
                </div>
                <div :class="profil" class="profil_background" v-if="data.name == this.name"
                    :style="{ 'background-image': 'url(' + imgUrl(data.images['webp']) + ')' }">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: 'Douglas Hurley',
            imgUrl(file) {
                return new URL(`../assets/img/crew/${file}`, import.meta.url).href;
            }
        }
    },
    methods: {
        page(name) {
            if (name == Crew['crew'][0].name) {
                return this.name = 'Douglas Hurley';
            } else if (name == Crew['crew'][1].name) {
                return this.name = 'Mark Shuttleworth';
            } else if (name == Crew['crew'][2].name) {
                return this.name = 'Victor Glover';
            } else if (name == Crew['crew'][3].name) {
                return this.name = 'Anousheh Ansari';
            }
        }
    },
    computed: {
        bulletOne() {
            return {
                focus: this.name == 'Douglas Hurley'
            }
        },
        bulletTwo() {
            return {
                focus: this.name == 'Mark Shuttleworth'
            }
        },
        bulletThree() {
            return {
                focus: this.name == 'Victor Glover'
            }
        },
        bulletFour() {
            return {
                focus: this.name == 'Anousheh Ansari'
            }
        },
        profil() {
            return {
                douglas: this.name == 'Douglas Hurley',
                mark: this.name == 'Mark Shuttleworth',
                victor: this.name == 'Victor Glover',
                anousheh: this.name == 'Anousheh Ansari'
            }
        }
    }
}
</script>

<style lang="scss" scoped>
.crew_layout {
    padding-bottom: 94px;

    .content {
        display: flex;
    }

    h5 {
        margin-bottom: 154px;
    }

    h4 {
        margin-bottom: 15px;
    }

    h3 {
        margin-bottom: 27px;
    }

    p {
        margin-bottom: 83px;
        width: 444px;
        height: 165px;
    }
}

.description {
    .bullet_list {
        display: flex;
        gap: 24px;

        span {
            content: "";
            width: 15px;
            height: auto;
            aspect-ratio: 1/1;
            border-radius: 15px;
            background: var(--color-3);
            mix-blend-mode: normal;
            opacity: 0.17;
            transition: .4s;

            &:hover {
                cursor: pointer;
                opacity: .5;
            }
        }
    }
}

.focus {
    opacity: 1 !important;
}

.profil_background {
    position: absolute;
    background-repeat: no-repeat;
    background-size: contain;
    width: 500px;
    filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));
}

.douglas {
    width: 568.07px;
    height: 712px;
    left: 616.93px;
    top: -24px;
}

.mark {
    width: 453.44px;
    height: 654px;
    left: 638px;
    top: 34px;
}

.victor {
    width: 554.39px;
    height: 681px;
    left: 565px;
    top: 37px;
}

.anousheh {
    width: 615.57px;
    height: 607px;
    left: 591px;
    top: 81px;
}

// transtions
.offsetX {
    animation: offsetX .7s ease;
}

@keyframes offsetX {
    from {
        transform: translateX(-50px);
    }

    to {
        transform: translateX(0px);
    }
}
</style>