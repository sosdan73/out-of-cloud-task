<template>
    <div
        class="container"
        :style="{ color, borderColor: color }"
    >
        <p>{{ text }}</p>
    </div>
</template>

<script>
    export default {
        props: {
            text: {
                type: String,
                default: 'Пустой контейнер'
            },
            color: {
                type: String,
                default: '#000'
            }
        }
    }
</script>

<style lang="scss" scoped>
.container {
    width: 100vw;
    border: 5px solid;
    box-sizing: border-box;

    display: flex;
    justify-content: center;
    align-items: center;

    font-weight: bold;

// Desktop
    @media (min-width: 1440px) {
        & {
            height: 150px;
            font-size: 2rem;
        }
    }
// Tablet
    @media (min-width: 1024px) and (max-width: 1439px) {
        & {
            height: 100px;
            font-size: 1.5rem;
        }
    }
// Mobile
    @media (max-width: 1023px) {
        & {
            height: 80px;
            font-size: 1.2rem;
        }
    }
}
</style>