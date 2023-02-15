<template>
    <div class="technology">
        <div class="technologie_layout">
            <h5><span>03</span>Space launch 101</h5>
            <div class="technology_container">
                <div class="number_choice">
                    <span>1</span>
                    <span>2</span>
                    <span>3</span>
                </div>
                <div class="description">
                    <h5>The terminology...</h5>
                    <h3>Launch vehicle</h3>
                    <p>A launch vehicle or carrier rocket is a rocket-propelled vehicle used to carry a
                        payload from Earth's surface to space, usually to Earth orbit or beyond. Our
                        WEB-X carrier rocket is the most powerful in operation. Standing 150 metres tall,
                        it's quite an awe-inspiring sight on the launch pad!</p>
                </div>
                <img src="../assets/img/technology/image-launch-vehicle-portrait.jpg" alt="">
            </div>
        </div>
    </div>
</template>

<script setup>

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

            &:active {
                background: var(--color-3);
                color: var(--color-1);
            }
        }
    }
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
</style>