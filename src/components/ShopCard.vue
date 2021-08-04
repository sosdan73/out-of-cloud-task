<template>
    <div class="card">
        <div
            class="card-image"
            :style="{ backgroundImage }"
        ></div>
        <div class="card-text">
            <h3 class="header">
                <slot name="header"></slot>
            </h3>
            <p class="description">
                <slot name="description"></slot>
            </p>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['image'],
        computed: {
            backgroundImage() {
                return 'url("/images/' + this.image + '.png")';
            }
        }
    }
</script>

<style lang="scss" scoped>
    .card {
        border: 1px solid #d0d4cd;
        box-sizing: border-box;
        display: flex;
        .card-image {
            background-color: #7db945;
            background-repeat: no-repeat;
            background-position: 50% 50%;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .card-text {
            width: 220px;
            .header {
                font-family: 'RotondaC Bold';
            }
        }
    }
    // Tablet and desktop
    @media (min-width: 1024px) {
        .card {
            padding: 30px 10px 24px 30px;
            gap: 30px;
            width: 390px;
            .card-image {
                width: 70px;
                height: 70px;
            }
            .header {
                font-size: 36px;
                line-height: 46px;
                margin-top: 10px;
            }
            .description {
                font-size: 16px;
                line-height: 24px;
            }
        }
    }
// Mobile
    @media (max-width: 1023px) {
        .card {
            width: 100%;
            margin: auto;
            max-width: 390px;
            padding: 30px 30px 25px 30px;
            flex-direction: column;
            justify-content: center;
            .card-image {
                width: 60px;
                height: 60px;
                margin: auto;
                margin-bottom: 20px;
            }
            .card-text {
                text-align: center;
                margin: auto;
                .header {
                    font-size: 30px;
                    line-height: 32px;
                }
                .description {
                    font-size: 14px;
                    line-height: 22px;
                }
            }
        }
    }
</style>