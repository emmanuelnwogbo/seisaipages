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
                    <div class="pill__topleft">
                        <h1 class="pill__topleft--h1">the pill</h1>
                        <div class="pill__topleft--body">
                            <p>As you take the pill and explore this new territory, there are somethings you must know. SaiSei is a brand that is for the Community. By the Community.</p>
                            <p>A collection of 8888 unique SAISEI SOLDIERS took the pill and vowed to never look back. We are currently lost in this new world they call “Metaverse” and we hope to find our way with the community.  Lets the journey begin.</p>
                        </div>
                    </div>
                    <div class="pill__topright">
                        <div></div>
                        <figure>
                            <img src="@/assets/imgs/frame.svg"/>
                            <img src="@/assets/imgs/top.svg"/>
                            <div class="pill__topright--circles">
                                <span :class="{
                                    'current': current === 1
                            }"></span>
                                <span :class="{
                                    'current': current === 2
                            }"></span>
                            </div>
                        </figure>
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
                current: 1
            }
        },
        methods: {
            togglecurrent() {
                this.current === 1 ? this.current = 2 : this.current = 1;
            }
        },
        computed: {
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

        @media only screen and (max-width: 414px) { 
            padding: 0 #{scaleValue(90)};
        }
        

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

                @media only screen and (max-width: 414px) { 
                    
                }
            } 

            &__top {
                display: flex;
                justify-content: space-between;
                min-height: #{scaleValue(800)};

                @media only screen and (max-width: 414px) { 
                    flex-direction: column;
                    min-height: #{scaleValue(3500)};
                    justify-content: flex-start;
                }
            }

            &__topleft {
                flex-basis: 50%;

                @media only screen and (max-width: 414px) { 
                    flex-basis: 100%;
                }

                &--h1 {
                    text-transform: uppercase;
                    font-size: #{scaleValue(128)};
                    margin-bottom: #{scaleValue(24)};

                    @media only screen and (max-width: 414px) { 
                        font-size: #{scaleValue(300)};
                        margin-bottom: #{scaleValue(100)};
                    }
                }

                &--body {
                    font-size: #{scaleValue(24)};
                    line-height: #{scaleValue(36)};

                    @media only screen and (max-width: 414px) { 
                        font-size: #{scaleValue(80)};
                        line-height: #{scaleValue(120)};
                    }

                    & p {
                        margin-bottom: #{scaleValue(24)};

                        @media only screen and (max-width: 414px) { 
                            margin-bottom: #{scaleValue(100)};
                        }
                    }
                }
            }

            &__topright {
                position: relative;
                flex-basis: 50%;
                display: flex;
                justify-content: space-between;

                @media only screen and (max-width: 414px) { 
                    flex-basis: 100%;
                }

                & figure {
                    position: relative;
                    height: #{scaleValue(700)};
                    width: #{scaleValue(530)};
                    justify-content: center;
                    display: flex;

                    @media only screen and (max-width: 414px) { 
                        flex-basis: 100%;
                    }

                    & img {
                        position: absolute;
                        top: 0;
                        right:0;
                        width: 100%;

                        &:nth-child(2) {
                            position: relative;
                            width: 91%;
                            height: #{scaleValue(533)};

                            @media only screen and (max-width: 414px) {
                                height: #{scaleValue(1430)};
                            }
                        }
                    }
                }

                &--circles {
                    position: absolute;
                    bottom: #{scaleValue(120)};
                    left: 0;
                    width: 100%;
                    display: flex;
                    justify-content: center;

                    @media only screen and (max-width: 414px) {
                        bottom: #{scaleValue(-920)};
                    }

                    & span {
                        display: inline-block;
                        height: #{scaleValue(20)};
                        width: #{scaleValue(20)};
                        border-radius: 100%;
                        border: 1px solid rgba(196, 196, 196, 1);
                        cursor: pointer;
                        margin: 0 #{scaleValue(5)};

                        @media only screen and (max-width: 414px) {
                            height: #{scaleValue(100)};
                            width: #{scaleValue(100)};
                            margin: 0 #{scaleValue(25)};
                        }

                        &.current {
                            background: rgba(196, 196, 196, 1);
                        }
                    }
                }
            }

            &__bottom {
                position: relative;

                @media only screen and (max-width: 414px) { 
                    margin-top: #{scaleValue(200)};
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