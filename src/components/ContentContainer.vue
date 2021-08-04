<template>
    <div class="container">
        <slider />
        <shop-section />
    </div>
</template>

<script>
    import slider from "./Slider.vue";
    import shopSection from "./ShopComponent.vue";

    export default {
        components: {
            slider,
            shopSection
        }
    }
</script>

<style lang="scss" scoped>
    .container {
        width: 100vw;
        .background-grey {
            background-color: #e5e5e5;
        }
    }
</style>