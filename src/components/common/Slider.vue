<template>
    <div v-if="slider.length > 0" class="slider">
        <div class="slider__items">
            <!-- Clone slide cuối lên vị trí đầu -->
            <div class="slider__item clone">
                <img :src="slider[slider.length - 1].image" :alt="slider[slider.length - 1].altImg">
            </div>

            <!-- Slide gốc -->
            <div v-for="(slide, i) in slider" :key="i" class="slider__item">
                <img :src="slide.image" :alt="slide.altImg">
            </div>

            <!-- Clone slide đầu xuống vị trí cuối -->
            <div class="slider__item clone">
                <img :src="slider[0].image" :alt="slider[0].altImg">
            </div>
        </div>

        <div class="slider__buttons-arrow">
            <div class="buttons-arror__container" id="container-left" @click="previous">
                <div class="buttons-arror__button" id="button-left">
                    <i class="fa-solid fa-chevron-left"></i>
                </div>
            </div>
            <div class="buttons-arror__container" id="container-right" @click="next">
                <div class="buttons-arror__button" id="button-right">
                    <i class="fa-solid fa-chevron-right"></i>
                </div>
            </div>
        </div>

        <ul class="slider__dots">
            <li 
            v-for="index in slider" 
            :key="index" 
            :class="{ active: index === indexOfCurrentSlideReal - 1 }"
            @click="goToPosition(index)"></li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Slider",
    data() {
        return {
            slider: [
                {
                    image: require("@/assets/images/slider/1.webp"),
                    altImg: "Slide 1"
                },
                {
                    image: require("@/assets/images/slider/2.webp"),
                    altImg: "Slide 2"
                },
                {
                    image: require("@/assets/images/slider/3.webp"),
                    altImg: "Slide 3"
                }
            ],
            indexOfCurrentSlideReal: 1,
            isConverting: false
        }
    },
    computed: {
        indexOfLastSlide() {
            return this.slider.length + 1
        }
    },
    methods: {
        next() {
            if (this.isConverting) 
                return

            this.indexOfCurrentSlideReal = this.indexOfCurrentSlideReal + 1
            this.reloadSlider()

            if (this.indexOfCurrentSlideReal > this.indexOfLastSlide - 1)
                this.handleTransitionEnd()
        },
        previous() {
            if (this.isConverting) 
                return

            this.indexOfCurrentSlideReal = this.indexOfCurrentSlideReal - 1
            this.reloadSlider()

            if (this.indexOfCurrentSlideReal < 1)
                this.handleTransitionEnd()
        },
        reloadSlider(withTransition = true) {
            const itemList = document.querySelector('.slider__items')
            const items = document.querySelectorAll('.slider__item')

            if(itemList) {
                // Áp dụng transition chỉ khi cần
                itemList.style.transition = withTransition ? 'transform 0.75s ease' : 'none'

                let slideWidth = items[this.indexOfCurrentSlideReal].offsetWidth
                const translateXValue = -this.indexOfCurrentSlideReal * slideWidth

                itemList.style.transform = `translateX(${translateXValue}px)`
                // itemList.style.transform = `translate3d(${translateXValue}px, 0px, 0px)`
                

                this.updateActiveDot()

                this.stopAutoSlide()
                this.startAutoSlide()
            }
        },
        updateActiveDot() {
            const dots = document.querySelectorAll('.slider__dots li')
            let lastActiveDot = document.querySelector('.slider__dots li.active')
            
            if (lastActiveDot)
                lastActiveDot.classList.remove('active')

            if (this.indexOfCurrentSlideReal > this.indexOfLastSlide - 1)
                dots[0].classList.add('active')
            else if (this.indexOfCurrentSlideReal < 1)
                dots[this.indexOfLastSlide - 2].classList.add('active')
            else
                dots[this.indexOfCurrentSlideReal - 1].classList.add('active')
        },
        startAutoSlide() {
            this.slideInterval = setInterval(() => {
                this.next();
            }, 4000)
        },
        stopAutoSlide() {
            clearInterval(this.slideInterval)
        },
        goToPosition(index) {
            this.indexOfCurrentSlideReal = index
            this.reloadSlider()
        },
        handleTransitionEnd() {
            // Đánh dấu đang trong quá trình đổi vị trí để bị spam cũng không sao
            this.isConverting = true

            // Thêm sự kiện lắng nghe kết thúc transition (vừa đến vị trí slide clone)
            const itemList = document.querySelector('.slider__items')
            itemList.addEventListener('transitionend', this.convertCloneToRealPosition, { once: true })
        },
        convertCloneToRealPosition() {
            // Convert từ vị trí slide clone về vị trí slide thật
            if (this.indexOfCurrentSlideReal > this.indexOfLastSlide - 1) {
                // Đã đến clone của slide đầu, nhảy về slide đầu thật
                this.indexOfCurrentSlideReal = 1
            } else if (this.indexOfCurrentSlideReal < 1) {
                // Đã đến clone của slide cuối, nhảy về slide cuối thật
                this.indexOfCurrentSlideReal = this.indexOfLastSlide - 1
            }

            // Tắt transition để nhảy ngay lập tức mà không nhìn thấy
            this.reloadSlider(false)

            // Bỏ đánh dấu đang đổi vị trí
            this.isConverting = false
        }
    },
    mounted() {
        this.$nextTick(() => {
            this.reloadSlider()
        })

        this.startAutoSlide()
    },
    beforeDestroy() {
        this.stopAutoSlide()
    }
}
</script>

<style scoped lang="scss">
$primary-background-color: #fff;
$secondary-background-color: #000;
$item-primary-color: #000;
$item-secondary-primary-color: #fff;
$item-secondary-color: #cb56b2;
$shadow-color: rgba(55, 55, 55, 0.35);

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.slider {
    display: flex;
    justify-content: center;
    width: calc(100vw - (100vw - 100%));
    height: fit-content;
    position: relative;
    overflow: hidden;

    &__items {
        display: flex;
        width: 100%;
        // transform: translate3d(0px, 0px, 0px);
        transform: translateX(0);
        transition: transform 0.75s ease;
    }

    &__item {
        display: flex;

        img {
            width: 100vw;
            height: auto;
        }
    }

    &__buttons-arrow {
        display: flex;
        justify-content: space-between;
        width: 100%;
        height: 100%;
        
        @media screen and (max-width: 768px) {
            display: none;
        }
        
        .buttons-arror__container {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 5em;
            height: 100%;
            position: absolute;
            z-index: 10;
            cursor: pointer;
            
            &#container-left {
                top: 0;
                left: 0;
            }

            &#container-right {
                top: 0;
                right: 0;
            }

            .buttons-arror__button {
                display: inline;
                padding: 0.625em 1em;
                box-shadow: 0 0 12px $shadow-color;
                color: $item-secondary-primary-color;
                border-radius: 50%;
                font-weight: lighter;
                font-size: larger;
                transition: all 0.2s ease-in;
            }

            &#container-left:active .buttons-arror__button#button-left,
            &#container-right:active .buttons-arror__button#button-right {
                box-shadow: inset 0 0 10px $shadow-color;
                opacity: 0.8;
            }

            &#container-left:hover .buttons-arror__button#button-left {
                transform: translateX(-4px);
            }

            &#container-right:hover .buttons-arror__button#button-right {
                transform: translateX(4px);
            }
        }
    }

    &__dots {
        display: flex;
        align-items: flex-end;
        justify-content: center;
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        z-index: 5;

        & li {
            list-style-type: none;
            width: 0.5em;
            height: 0.5em;
            background-color: $primary-background-color;
            margin: 1em 0.75em;
            border-radius: 20px;
            transition: all 0.75s ease;
            cursor: pointer;

            &.active {
                width: 2em;
            }
        }
    }
}
</style>