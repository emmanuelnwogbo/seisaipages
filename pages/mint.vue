<template>
    <div>
        <div class="pill">
            <header class="pill__header">
                <figure class="pill__header--logo">
                    <img src="@/assets/imgs/logo.svg" />
                </figure>
            </header>
            <div class="pill__container">
                <div class="pill__top">
                    <div class="pill__top--figs">
                        <figure>
                            <img src="@/assets/imgs/leftmint.svg"/>
                        </figure>
                        <figure>
                            <img src="@/assets/imgs/rightmint.svg"/>
                        </figure>
                    </div>
                    <div class="pill__top--mintprice">
                        <span class="price">{{mintprice}}ETH</span>
                        <div class="pill__top--mintpricetoggle">
                            <span @click="incrmint">+</span>
                            <span>{{mintquantity}}</span>
                            <span @click="redumint">-</span>
                        </div>
                    </div>
                    <div class="pill__top--mintbtn">
                        <button>mint</button>
                    </div>
                </div>
                <div class="pill__bottom">
                    <div class="pill__bottom--slidetems">
                        <div class="pill__bottom--rightarrow">
                            <figure @click="togglecurrent">
                                <img src="@/assets/imgs/rightarrow.svg"/>
                            </figure>
                        </div>
                        <Slide v-for="item in slidetems" 
                        :item="item" 
                        :current="current"
                        v-bind:key="item.id"
                        />
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                current: 1,
                mintquantity: 1
            }
        },
        methods: {
            togglecurrent() {
                this.current === 1 ? this.current = 2 : this.current = 1;
            },
            incrmint() {
                let mintquantity = this.mintquantity;
                mintquantity+=1;
                this.mintquantity = mintquantity;
            },
            redumint() {
                if (this.mintquantity === 1) {
                    return;
                } else {
                    let mintquantity = this.mintquantity;
                    mintquantity-=1;
                    this.mintquantity = mintquantity;
                }
            }
        },
        computed: {
            mintprice() {
                return Math.round((0.006 * this.mintquantity) * 1000) / 1000
            },
            slidetems() {
                return [
                    {
                        id: 1,
                        img() {
                            return `${require('@/assets/imgs/slide1.svg')}`
                        },
                        background: 'rgba(17, 97, 97, 1)',
                        itembackground: 'rgba(196, 196, 196, 0.18)',
                        traits: [{
                            heading: 'body',
                            label: 'body type1'
                        },
                        {
                            heading: 'face',
                            label: 'empty face'
                        },
                        {
                            heading: 'eye',
                            label: 'focused red eyes'
                        },
                        {
                            heading: 'clothing',
                            label: 'cyan leather jacket'
                        },
                        {
                            heading: 'mouth',
                            label: 'smirk'
                        },
                        {
                            heading: 'hair',
                            label: 'gold bob cut'
                        },
                        {
                            heading: 'eye wear',
                            label: 'no eyewear'
                        },
                        {
                            heading: 'ear',
                            label: 'gold ring2'
                        },
                        {
                            heading: 'hand',
                            label: 'wine'
                        },
                        {
                            heading: 'environ',
                            label: 'rain'
                        }]
                    },
                    {
                        id: 2,
                        img() {
                            return `${require('@/assets/imgs/slide2.svg')}`
                        },
                        background: 'rgba(133, 13, 24, 1)',
                        itembackground: 'rgba(196, 196, 196, 0.18)',
                        traits: [{
                            heading: 'body',
                            label: 'body type4'
                        },
                        {
                            heading: 'face',
                            label: 'empty face'
                        },
                        {
                            heading: 'eye',
                            label: 'focused blue eyes'
                        },
                        {
                            heading: 'clothing',
                            label: 'blue kimono'
                        },
                        {
                            heading: 'mouth',
                            label: 'slightly opened'
                        },
                        {
                            heading: 'hair',
                            label: 'black bob cut'
                        },
                        {
                            heading: 'eye wear',
                            label: 'VR'
                        },
                        {
                            heading: 'ear',
                            label: 'gold hook'
                        },
                        {
                            heading: 'hand',
                            label: 'no hand'
                        },
                        {
                            heading: 'environ',
                            label: 'rain'
                        }]
                    }
                ]
            }
        }
    }
</script>

<style lang="scss" scoped>
@function scaleValue($value) {
    @return calc(
      #{$value} * (clamp(350px, 100vw, 3840px) / var(--ideal-viewport-width))
    );
}

    .pill {
        color: #fff;
        padding: 0 #{scaleValue(90)};
        min-height: 100vh;

            &__header {
                position: fixed;
                top: 0;
                left: 0;
                z-index: 5;
                width: 100vw;
                display: flex;
                justify-content: space-between;
                background: #1F1D2B;
                height: #{scaleValue(90)};
                overflow: hidden;

                &--logo {
                    cursor: pointer;
                }
            }

            &__container {
                position: relative;
                padding-top: #{scaleValue(150)};
            } 

            &__top {
                display: flex;
                flex-direction: column;
                height: #{scaleValue(800)};
                padding: 0 #{scaleValue(290)};
                align-items: center;

                @media only screen and (max-width: 414px) { 
                    padding: 0;
                    align-items: center;

                    height: #{scaleValue(1700)}
                }

                &--figs {
                    display: flex;
                    justify-content: space-between;
                    width: #{scaleValue(840)};
                    margin-bottom: #{scaleValue(40)};

                    @media only screen and (max-width: 414px) { 
                        width: 100%;
                    }

                    & figure {
                        
                        & img {
                            @media only screen and (max-width: 414px) { 
                                height: #{scaleValue(700)};
                            }
                        }
                    }
                }

                &--mintprice {
                    display: flex;
                    flex-direction: column;
                    align-items: center;

                    & span {
                        display: inline-block;
                        font-size: #{scaleValue(40)};

                        @media only screen and (max-width: 414px) { 
                            font-size: #{scaleValue(150)};
                        }

                        &.price {
                            margin-bottom: #{scaleValue(20)};
                        }
                    }
                }

                &--mintpricetoggle {
                    position: relative;
                    display: flex;
                    align-items: center;
                    justify-content: center;
                    background: #fff;
                    border-radius: 3rem;
                    width: #{scaleValue(270)};
                    color: #000000;
                    text-align: center;
                    padding: #{scaleValue(15)} #{scaleValue(20)};
                    margin-bottom: #{scaleValue(20)};

                    @media only screen and (max-width: 414px) { 
                        justify-content: space-between;
                        width: #{scaleValue(900)};
                        padding: #{scaleValue(15)} #{scaleValue(70)};
                        margin-bottom: #{scaleValue(100)};
                    }

                    &:before {
                        content: '';
                        position: absolute;
                        background: rgba(196, 196, 196, 1);
                        width: 1px;
                        height: 100%;
                        left: #{scaleValue(60)};

                        @media only screen and (max-width: 414px) { 
                            left: #{scaleValue(130)};
                        }
                    }

                    &:after {
                        content: '';
                        position: absolute;
                        background: rgba(196, 196, 196, 1);
                        width: 1px;
                        height: 100%;
                        right: #{scaleValue(60)};

                        @media only screen and (max-width: 414px) { 
                            right: #{scaleValue(130)};
                        }
                    }

                    & span {
                        display: inline-block;

                        &:nth-child(1) {
                            transform: translateX(#{scaleValue(-60)});
                            cursor: pointer;
                            padding: 0 #{scaleValue(20)};

                            @media only screen and (max-width: 414px) { 
                                font-size: #{scaleValue(140)};
                            }
                        }

                        &:nth-child(3) {
                            transform: translateX(#{scaleValue(60)});
                            cursor: pointer;
                            font-size: #{scaleValue(45)};
                            padding: 0 #{scaleValue(20)};

                            @media only screen and (max-width: 414px) { 
                                font-size: #{scaleValue(160)};
                            }
                        }
                    }
                }

                &--mintbtn {      

                    & button {
                        background: rgba(19, 52, 99, 1);
                        color: #fff;
                        border: none;
                        outline: none;
                        text-transform: uppercase;
                        font-size: #{scaleValue(40)};
                        border-radius: 3rem;
                        width: #{scaleValue(300)};
                        height: #{scaleValue(80)};
                        cursor: pointer;

                        @media only screen and (max-width: 414px) { 
                            width: #{scaleValue(900)};
                            height: #{scaleValue(220)};
                            font-size: #{scaleValue(90)};
                        }
                    }
                }
            }

            &__bottom {
                position: relative;

                @media only screen and (max-width: 414px) { 
                    //display: none
                }
                
                &--slidetems {
                    position: relative;
                    display: flex;
                }

                &--rightarrow {
                    position: absolute;
                    top: 0;
                    right: 0;
                    height: #{scaleValue(900)};
                    display: flex;
                    align-items: center;
                    z-index: 3;

                    & figure {
                        transform: translateX(#{scaleValue(55)});
                        cursor: pointer;

                        @media only screen and (max-width: 414px) { 
                            
                            & img {
                                height: #{scaleValue(330)};
                            }
                        }
                    }
                }
            }
    }
</style>