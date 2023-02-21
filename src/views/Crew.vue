<script setup>
import Crew from '@/assets/data/data.json'
</script>

<template>
    <div class="crew">
        <div class="crew_layout">
            <h5><span>02</span>Meet your crew</h5>
            <div class="content" v-for="data in Crew.crew">
                <div class="description" v-if="data.name == this.name">
                    <h4 v-if="data.role" class="offsetX">{{ data.role }}</h4>
                    <h3 v-if="data.name" class="offsetX">{{ data.name }}</h3>
                    <p v-if="data.bio" :class="width" class="offsetX">{{ data.bio }}</p>
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
        },
        width() {
            return {
                douglasText: this.name == 'Douglas Hurley',
                markText: this.name == 'Mark Shuttleworth',
                victorText: this.name == 'Victor Glover',
                anoushehText: this.name == 'Anousheh Ansari'
            }
        }
    }
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/responsive.scss';

.crew_layout {
    padding-bottom: 94px;

    h5 {
        margin-bottom: 154px;

        @media #{$tabletLandscape} {
            margin-bottom: 60px;
        }
    }

    .content {
        display: flex;

        @media #{$tabletLandscape} {
            flex-direction: column;
        }

        @media #{$mobileDownScreen} {
            flex-direction: column-reverse;
        }
    }

    h4 {
        margin-bottom: 15px;

        @media #{$tabletLandscape} {
            margin-bottom: 8px;
        }

        @media #{$mobileDownScreen} {
            margin-top: 32px;
        }
    }

    h3 {
        margin-bottom: 27px;

        @media #{$tabletLandscape} {
            margin-bottom: 16px;
        }
    }

    p {
        margin-bottom: 83px;
        width: 444px;
        height: 165px;

        @media #{$tabletLandscape} {
            margin: 0 auto 40px;
            height: initial;
        }

        @media #{$mobileDownScreen} {
            font-size: 15px;
            line-height: 25px;
            width: 327px;
            margin: 0;
        }
    }

    @media #{$tabletPortrait} {
        .douglasText {
            width: 458px;
        }

        .markText {
            width: 520px;
        }

        .victorText {
            width: 592px;
        }

        .anoushehText {
            width: 536px;
        }
    }

    .douglasText,
    .markText,
    .victorText,
    .anoushehText {
        @media #{$mobileUpScreen} {
            width: auto;
        }
    }

    h4,
    h3,
    p,
    .bullet_list {
        @media #{$tabletLandscape} {
            display: flex;
            place-content: center;
            text-align: center;
        }
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

            &:active {
                opacity: .5;
            }

            @media #{$tactilUpScreen} {
                &:hover {
                    cursor: pointer;
                    opacity: .5;
                }
            }

            @media #{$tabletLandscape} {
                width: 10px;
                margin-bottom: 40px;
            }

            @media #{$mobileDownScreen} {
                margin: 32px 0;
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
    filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));

    @media #{$tabletLandscape} {
        position: relative;
        left: 0 !important;
        top: 0 !important;
        background-position-x: center;
        margin: auto;
    }
}

.douglas {
    width: 568px;
    height: 712px;
    left: 734px;
    bottom: 0;

    @media #{$desktopMediumScreen} {
        width: 368px;
        height: 512px;
        left: 634px;
        bottom: -10px;
    }

    @media #{$tabletLandscape} {
        width: 456px;
        height: 572px;
    }

    @media #{$mobileMediumScreen} {
        width: 306px;
        height: 422px;
    }

    @media #{$mobileDownScreen} {
        width: 327px;
        height: 223px;
    }
}

.mark {
    width: 453px;
    height: 654px;
    left: 800px;
    bottom: 0;

    @media #{$desktopMediumScreen} {
        width: 253px;
        height: 412px;
        left: 634px;
        bottom: -38px;
    }

    @media #{$tabletLandscape} {
        width: 368px;
        height: 532px;
    }

    @media #{$mobileMediumScreen} {
        width: 300px;
        height: 382px;
    }

    @media #{$mobileDownScreen} {
        width: 327px;
        height: 223px;
    }
}

.victor {
    width: 554px;
    height: 681px;
    left: 743px;
    bottom: 0;

    @media #{$desktopMediumScreen} {
        width: 354px;
        height: 481px;
        left: 559px;
        bottom: -65px;
    }

    @media #{$tabletLandscape} {
        width: 453px;
        height: 532px;
    }

    @media #{$mobileMediumScreen} {
        width: 306px;
        height: 382px;
    }

    @media #{$mobileDownScreen} {
        width: 327px;
        height: 223px;
    }
}

.anousheh {
    width: 615px;
    height: 607px;
    left: 735px;
    bottom: 0;

    @media #{$desktopMediumScreen} {
        width: 415px;
        height: 407px;
        left: 586px;
    }

    @media #{$tabletLandscape} {
        width: 539px;
        height: 532px;
    }

    @media #{$mobileUpScreen} {
        width: 416px;
        height: 382px;
    }

    @media #{$mobileMediumScreen} {
        width: 306px;
        height: 422px;
    }

    @media #{$mobileDownScreen} {
        width: 327px;
        height: 223px;
    }
}

// transtions
.offsetX {
    animation: offsetX .7s ease;

    @media #{$tabletPortrait} {
        animation: offsetY .7s ease;
    }
}

@keyframes offsetX {
    from {
        transform: translateX(-50px);
    }

    to {
        transform: translateX(0px);
    }
}

@keyframes offsetY {
    from {
        transform: translateY(-25px);
    }

    to {
        transform: translateY(0px);
    }
}
</style>