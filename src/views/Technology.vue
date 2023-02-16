<script setup>
import Technology from '@/assets/data/data.json'
</script>

<template>
    <div class="technology">
        <div class="technologie_layout">
            <h5><span>03</span>Space launch 101</h5>
            <div class="content" v-for="data in Technology.technology">
                <div class="technology_container" v-if="data.name == this.name">
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
                    <img class="offsetYtop" :src="imgUrl(data.images['portrait'])"
                        :alt="data.name + ' technology image'" v-if="data.images['portrait']">
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
.technologie_layout {
    padding-bottom: 101px;
    width: 100%;

    &>h5 {
        margin-bottom: 26px;
    }
}

.technology_container {
    display: flex;
    place-items: center;
    place-content: space-between;

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

            &:hover {
                cursor: pointer;
                border: 1px solid var(--color-3);
            }
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
    }

    h3 {
        margin-bottom: 17px;
    }

    p {
        width: 444px;
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