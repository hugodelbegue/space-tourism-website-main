<template>
    <div class="crew">
        <div class="crew_layout">
            <div class="description">
                <h5><span>02</span>Meet your crew</h5>
                <h4>Commander</h4>
                <h3>Douglas Hurley</h3>
                <p>Douglas Gerald Hurley is an American engineer, former Marine Corps pilot
                    and former NASA astronaut. He launched into space for the third time as
                    commander of Crew Dragon Demo-2.</p>
                <div class="bullet_list">
                    <span></span>
                    <span></span>
                    <span></span>
                    <span></span>
                </div>
            </div>
            <div class="profil_background"></div>
        </div>
    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>
.crew_layout {
    padding-top: 76px;
    padding-left: 166.5px;
    padding-bottom: 94px;
    display: flex;
    width: 100%;

    h5 {
        margin-bottom: 154px;

        span {
            mix-blend-mode: normal;
            opacity: 0.25;
            margin-right: 28px;
        }
    }

    h4 {
        color: var(--color-3);
        mix-blend-mode: normal;
        opacity: 0.5;
        margin-bottom: 15px;
    }

    h3 {
        margin-bottom: 27px;
    }

    p {
        font-size: 18px;
        margin-bottom: 120px;
        color: var(--color-2);
        width: 444px;
    }
}

.description {

    .bullet_list {
        display: flex;
        gap: 24px;

        span {
            content: "";
            width: 15px;
            height: 15px;
            border-radius: 15px;
            background: var(--color-3);
            mix-blend-mode: normal;
            opacity: 0.17;
        }
    }
}

.profil_background {
    position: absolute;
    width: 1273.51px;
    height: 700px;
    background-image: url(../assets/img/crew/image-douglas-hurley.png);
    background-repeat: no-repeat;
    background-size: auto;
    background-position-x: 81%;
}
</style>