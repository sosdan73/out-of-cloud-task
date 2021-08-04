<template>
    <div class="background-grey">
        <div class="slider-container">
            <h2 class="header" v-html="sliderHeader"></h2>
            <div class="slider-grid">
                <div
                    class="slider-arrow-left"
                    @click="showPreviousSlide"
                >
                    <img
                        src="/images/arrow.png"
                        alt
                        class="arrow arrow-left"
                    >
                </div>
                <div class="slider-card-container">
                    <numbered-image :slideInfo="sliderData[currentId - 1]" />
                    <div class="slider-card-content">
                        <p class="bold">{{ sliderData[currentId - 1].title }}</p>
                        <p>{{ sliderData[currentId - 1].description }}</p>
                    </div>
                </div>
                <div
                    class="slider-arrow-right"
                    @click="showNextSlide"
                >
                    <img
                        src="/images/arrow.png"
                        alt
                        class="arrow arrow-right"
                    >
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import numberedImage from "./NumberedImage.vue";

    export default {
        components: {
            numberedImage
        },
        data() {
            return {
                sliderData: [
                    {
                        id: 1,
                        image: 'image1',
                        title: 'Привезем точно по списку',
                        description: 'Сборщик берёт с собой наручный терминал, на котором он видит весь список покупок каждого заказа.'
                    },
                    {
                        id: 2,
                        image: 'image2',
                        title: 'Собираем быстро и эффективно',
                        description: 'Для улучшения эргономики пространства товары размещены от тяжелых к лёгким, находящимся уже в конечной зоне упаковки.'
                    },
                    {
                        id: 3,
                        image: 'image3',
                        title: 'За свежесть и качество отвечаем',
                        description: 'Выделены специальные зоны, в том числе холодная и морозильная.'
                    },
                    {
                        id: 4,
                        image: 'image4',
                        title: 'Шампунь не положат рядом с рыбой',
                        description: 'Собираем и упаковываем ваш заказ с заботой: соблюдаем принципы товарного соседства и учитываем вес товара.'
                    },
                    {
                        id: 5,
                        image: 'image5',
                        title: 'Довезём в сохранности даже яйца',
                        description: 'Бережно транспортируем контейнеры, фиксируя из стяжными ремнями. Системы охлаждения поддерживают температурный режим.'
                    },
                ],
                currentId: 1,
            }
        },
        methods: {
            showPreviousSlide() {
                // При перелистывании назад с первого слайда прибавляется 4, чтобы получить 5, в противном случае вычитается 1
                this.currentId -= this.currentId == 1 ? -4 : 1;
            },
            showNextSlide() {
                // При перелистывании вперед с пятого слайда вычитается 4, чтобы получить 1, в противном случае прибавляется 1
                this.currentId += this.currentId == 5 ? -4 : 1;
            }
        },
        computed: {
            // Нужно для соблюдения дизайн-макета
            sliderHeader() {
                if (innerWidth > 1023) {
                    return 'Взгляните на процесс сборки<br>своими глазами'
                } else {
                    return 'Взгляните на процесс сборки своими глазами'
                }
            }
        },
    }
</script>

<style lang="scss" scoped>
    .background-grey {
        background-color: #e5e5e5;
        .slider-container {
            margin: auto;
            .header {
                text-align: center;
            }
            .slider-grid {
                display: grid;
                .arrow {
                    cursor: pointer;
                }
                .slider-arrow-left {
                    grid-area: left-arrow;
                }
                .slider-card-container {
                    background-color: #fff;
                    grid-area: card;
                    box-sizing: border-box;
                    border-radius: 10px;
                    box-shadow: 0 0 40px rgba(0, 0, 0, 0.1);
                    text-align: center;
                }
                .slider-arrow-right {
                    grid-area: right-arrow;
                    .arrow-right {
                        transform: rotate(180deg);
                    }
                }
            }
        }
    }
// Tablet and desktop
    @media (min-width: 1024px) {
        .slider-container {
            width: 740px;
            padding-top: 73px;
            padding-bottom: 80px;
            .header {
                margin-bottom: 29px;
                font-size: 36px;
                line-height: 46px;
            }
            .slider-grid {
                grid-template-areas: "left-arrow card right-arrow";
                justify-content: center;
                align-items: center;
                gap: 30px;
                .arrow {
                    width: 20px;
                    height: 40px;
                }
                .slider-card-container {
                    width: 640px;
                    padding: 40px;
                    .slider-card-content {
                        // padding: 0 30px;
                        font-size: 16px;
                        line-height: 24px;
                    }
                }
            }
        }
    }
// Desktop
    @media (min-width: 1440px) {
        .slider-container {
            padding-top: 129px;
        }
    }
// Tablet
    @media (min-width: 1024px) and (max-width: 1439px) {
        .slider-container {
            padding-top: 73px;
        }
    }
// Mobile
    @media (max-width: 1023px) {
        .slider-container {
            padding: 50px 20px;
            .header {
                font-size: 26px;
                line-height: 32px;
                margin-bottom: 32px;
            }
            .slider-grid {
                grid-template-areas:    "card card"
                                        "left-arrow right-arrow";
                gap: 33px 60.71px;
                .slider-arrow-left {
                    justify-self: end;
                }
                .arrow {
                    width: 14.29px;
                    height: 28.57px;
                }
                .slider-card-container {
                    width: 100%;
                    padding: 20px;
                    .slider-card-content {
                        padding: 0 20px;
                        font-size: 14px;
                        line-height: 22px;
                    }
                }
            }
        }
    }
</style>