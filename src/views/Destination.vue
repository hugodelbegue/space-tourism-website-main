<script setup>

</script>

<template>
    <div class="destination">
        <div class="destination_layout">
            <h5><span>01</span>Pick your destination</h5>
            <div class="destination_container">
                <div class="picture_container">
                    <img src="../assets/img/destination/image-moon.png" alt="">
                </div>
                <div class="description">
                    <div class="planet_nav">
                        <ul>
                            <li>Moon</li>
                            <li>Mars</li>
                            <li>Europa</li>
                            <li>Titan</li>
                        </ul>
                    </div>
                    <h2>Moon</h2>
                    <p> See our planet as you’ve never seen it before. A perfect relaxing trip away to help
                        regain perspective and come back refreshed. While you’re there, take in some history
                        by visiting the Luna 2 and Apollo 11 landing sites.</p>
                    <hr>
                    <div class="statistics">
                        <div class="distance">
                            <div class="indicative">Avg. distance</div>
                            <span class="number">384,400 km</span>
                        </div>
                        <div class="time">
                            <div class="indicative">Est. travel time</div>
                            <span class="number">3 days</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.destination_layout {
    padding-top: 76px;
    padding-left: 166.5px;
    padding-right: 163px;
    padding-bottom: 118px;

    h2 {
        line-height: 115px;
        margin: 37px 0 14px;
    }

    h5 {
        margin-bottom: 64px;

        span {
            mix-blend-mode: normal;
            opacity: 0.25;
            margin-right: 28px;
        }
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

    p {
        font-size: 18px;
        line-height: 32px;
        color: var(--color-2);
    }

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
            transition: .3s;

            &:hover {
                cursor: pointer;
                border-bottom: 3px solid var(--color-3);
            }
        }
    }
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
</style>