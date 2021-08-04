<template>
    <div class="shop-container">
        <div class="shop-cards">
            <card image="sale">
                <template v-slot:header>
                    Скидка <span class="text-green">1500&#8381;</span>
                </template>
                <template v-slot:description>
                    <span class="bold">-500 &#8381;</span> на первые три заказа по промокоду NEW
                </template>
            </card>
            <span class="bold plus-icon">+</span>
            <card image="delivery">
                <template v-slot:header>
                    Бесплатная <span class="text-green">доставка</span>
                </template>
                <template v-slot:description>
                    первого заказа
                </template>
            </card>
        </div>
        <popup-component />
    </div>
</template>

<script>
    import card from "./ShopCard.vue";
    import popupComponent from "./PopUpComponent.vue";

    export default {
        components: {
            card,
            popupComponent
        }
    }
</script>

<style lang="scss" scoped>
    .shop-cards {
        display: flex;
        justify-content: center;
        .plus-icon {
            font-size: 36px;
            line-height: 46px;
            align-self: center;
        }
    }
// Tablet and desktop
    @media (min-width: 1024px) {
        .shop-container {
            padding-top: 60px;
            padding-bottom: 100px;
            .shop-cards {
                gap: 3vw;
            }
        }
    }
// Mobile
    @media (max-width: 1023px) {
        .shop-container {
            padding: 30px 20px 80px;
            .shop-cards {
                gap: 20px;
                flex-direction: column;
            }
        }
    }
</style>