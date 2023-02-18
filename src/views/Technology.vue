<script setup>
import Technology from '@/assets/data/data.json'
</script>

<template>
    <div class="technology">
        <div class="technologie_layout">
            <h5><span>03</span>Space launch 101</h5>
            <div class="content" v-for="data in Technology.technology">
                <div class="technology_container" v-if="data.name == this.name">
                    <div class="description_container">
                        <div class="number_choice">
                            <span @click="page('Launch vehicle')" :class="vehicle">1</span>
                            <span @click="page('Spaceport')" :class="spaceport">2</span>
                            <span @click="page('Space capsule')" :class="capsule">3</span>
                        </div>
                        <div class="description offsetYbottom" v-if="data.name && data.description">
                            <h5>The terminology...</h5>
                            <h3>{{ data.name }}</h3>
                            <p>{{ data.description }}</p>
                        </div>
                    </div>
                    <img class="offsetYtop portrait" :src="imgUrl(data.images['portrait'])"
                        :alt="data.name + ' technology image'" v-if="data.images['portrait']">
                    <img class="offsetYtop landscape" :src="imgUrl(data.images['landscape'])"
                        :alt="data.name + ' technology image'" v-if="data.images['landscape']">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: 'Launch vehicle',
            cla: '',
            imgUrl(file) {
                return new URL(`../assets/img/technology/${file}`, import.meta.url).href;
            }
        }
    },
    methods: {
        page(name) {
            if (name == Technology['technology'][0].name) {
                return this.name = 'Launch vehicle';
            } else if (name == Technology['technology'][1].name) {
                return this.name = 'Spaceport';
            } else if (name == Technology['technology'][2].name) {
                return this.name = 'Space capsule';
            }
        }
    },
    computed: {
        vehicle() {
            return {
                focus: this.name == 'Launch vehicle'
            }
        },
        spaceport() {
            return {
                focus: this.name == 'Spaceport'
            }
        },
        capsule() {
            return {
                focus: this.name == 'Space capsule'
            }
        },
    }
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/responsive.scss';

.technologie_layout {
    padding-bottom: 101px;
    width: 100%;

    &>h5 {
        margin-bottom: 26px;

        @media #{$tabletLandscape} {
            margin-bottom: 60px;
        }
    }
}

.technology_container {
    display: flex;
    place-items: center;
    place-content: space-between;

    @media #{$tabletLandscape} {
        flex-direction: column-reverse;
    }

    .description_container {
        display: flex;
        gap: 80px;

        @media #{$tabletPortrait} {
            flex-direction: column;
            gap: 44px;
        }

        @media #{$mobileDownScreen} {
            gap: 26px;
        }
    }

    .number_choice {
        display: flex;
        flex-direction: column;
        gap: 32px;

        span {
            display: flex;
            place-items: center;
            place-content: center;
            width: 80px;
            height: auto;
            aspect-ratio: 1/1;
            border-radius: 80px;
            mix-blend-mode: normal;
            font-size: 32px;
            line-height: 37px;
            border: 1px solid var(--color-3-shadow);
            font-family: var(--font-family-heading);
            transition: .3s;

            &:active {
                border: 1px solid var(--color-3);
            }

            @media #{$tactilUpScreen} {
                &:hover {
                    cursor: pointer;
                    border: 1px solid var(--color-3);
                }
            }

            @media #{$tabletPortrait} {
                width: 60px;
                font-size: 24px;
                line-height: 28px;
            }

            @media #{$mobileDownScreen} {
                width: 40px;
                font-size: 16px;
                line-height: 18px;
            }
        }

        @media #{$tabletPortrait} {
            flex-direction: row;
            place-content: center;
        }
    }
}

.focus {
    background: var(--color-3) !important;
    color: var(--color-1) !important;
}

.description {
    width: 470px;

    h5 {
        color: var(--color-2);
        font-size: 16px;
        line-height: 19px;
        letter-spacing: 2.7px;
        margin-bottom: 11px;

        @media #{$tabletPortrait} {
            margin-bottom: 16px;
        }

        @media #{$mobileDownScreen} {
            margin-bottom: 9px !important;
        }
    }

    h3 {
        margin-bottom: 17px;

        @media #{$desktopDownScreen} {
            font-size: 40px;
        }

        @media #{$tabletPortrait} {
            font-size: 40px;
            line-height: 46px;
            margin-bottom: 16px;
        }

        @media #{$mobileDownScreen} {
            font-size: 24px;
            line-height: 28px;
        }
    }

    p {
        width: 444px;

        @media #{$desktopDownScreen} {
            width: 385px !important;
        }

        @media #{$tabletPortrait} {
            width: initial !important;
        }

        @media #{$mobileDownScreen} {
            width: 327px !important;
        }
    }

    @media #{$desktopDownScreen} {
        width: 415px;
    }

    @media #{$tabletPortrait} {
        text-align: center;
        width: 458px;
    }
}

img {
    @media #{$desktopMediumScreen} {
        width: 380px;
    }

    @media #{$desktopDownScreen} {
        width: 350px;
    }

    @media #{$tabletLandscape} {
        margin-bottom: 56px;
        align-self: center;
        width: calc(100% + (39px*2));
    }

    @media #{$mobileDownScreen} {
        margin-bottom: 34px;
    }
}

.portrait {
    display: block;

    @media #{$tabletLandscape} {
        display: none;
    }
}

.landscape {
    display: none;

    @media #{$tabletLandscape} {
        display: block;
    }
}

// transitions
.offsetYtop {
    animation: offsetYtop .7s ease;
}

.offsetYbottom {
    animation: offsetYbottom .7s ease;
}

@keyframes offsetYtop {
    from {
        transform: translateY(-25px);
    }

    to {
        transform: translateY(0px);
    }
}

@keyframes offsetYbottom {
    from {
        transform: translateY(25px);
    }

    to {
        transform: translateY(0px);
    }
}
</style>