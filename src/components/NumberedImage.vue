<template>
    <div
        class="image-container"
        :style="{ backgroundImage }"
    >
        <div class="number-container">
            <span class="text-green bold number">{{ slideInfo.id }}</span>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['slideInfo'],
        computed: {
            backgroundImage() {
                return 'url("/images/slider/' + this.slideInfo.image + '.jpg")'; 
            }
        }
    }
</script>

<style lang="scss" scoped>
    .image-container {
        position: relative;
        width: 100%;
        background-size: cover;
        .number-container {
            position: absolute;
            border-radius: 50%;
            background-color: #fff;
            display: flex;
            justify-content: center;
            align-items: center;
        }
    }
// Tablet and desktop
    @media (min-width: 1024px) {
        .image-container {
            height: 284px;
            margin-bottom: 28px;
            .number-container {
                width: 50px;
                height: 50px;
                font-size: 22px;
                line-height: 46px;
                top: -12px;
                left: -4px;
                .number {
                    position: relative;
                    top: 3px;
                    left: 1px;
                }
            }
        }
    }
// Mobile
    @media (max-width: 1023px) {
        .image-container {
            height: 160px;
            margin-bottom: 20px;
            .number-container {
                width: 40px;
                height: 40px;
                font-size: 16px;
                line-height: 46px;
                top: -9px;
                left: -8px;
                .number {
                    position: relative;
                    top: 3px;
                    left: 2px;
                }
            }
        }
    }
</style>