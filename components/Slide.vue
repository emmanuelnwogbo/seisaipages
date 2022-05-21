<template>
<div class="slide" :style="{ 
    background: item.background,
    opacity: current === item.id ? '1' : '0',
    transform: current === item.id ? 'translateX(0)' : 'translateX(100%)'
 }">
            <div class="slide__left">
                <figure>
                    <img :src="item.img()"/>
                </figure>
            </div>
            <div class="slide__right">
                <div class="slide__right--item" v-for="trait in item.traits" 
                :style="{ background: item.itembackground }">
                    <div class="slide__right--itemhd">
                        <p>{{trait.heading}}</p>
                    </div>
                    <div class="slide__right--itemlb">
                        <p>{{trait.label}}</p>
                    </div>
                </div>
            </div>
        </div>
</template>

<script>
    export default {
        data() {
            return {}
        },
        props: ['item', 'current'],
        mounted() {
            console.log(this.item, 'hello item')
        }
    }
</script>

<style lang="scss" scoped>
@function scaleValue($value) {
    @return calc(
      #{$value} * (clamp(350px, 100vw, 3840px) / var(--ideal-viewport-width))
    );
}

    .slide {
        display: flex;
        justify-content: space-between;
        border-radius: 2rem;
        padding: #{scaleValue(120)} #{scaleValue(60)};
        align-items: top;
        flex-shrink: 0;
        width: 100%;
        transition: all .2s ease;
        position: absolute;
        top: 0;
        left: 0;

        @media only screen and (max-width: 414px) { 
           flex-direction: column;
           padding: #{scaleValue(50)};
           justify-content: center;
        }

        &__left {

            & figure {

                @media only screen and (max-width: 414px) { 
                    width: #{scaleValue(1300)};

                    & img {
                        width: 100%;
                        height: 100%;
                    }
                }
            }
        }

        &__right {
            display: flex;
            flex-wrap: wrap;
            flex-basis: #{scaleValue(700)};

            @media only screen and (max-width: 414px) { 
                margin-top: #{scaleValue(100)};
            }

            &--item {
                display: flex;
                flex-direction: column;
                justify-content: space-between;
                text-align: center;
                border-radius: 1rem;
                margin-bottom: #{scaleValue(30)};
                flex-basis: #{scaleValue(300)};
                min-height: #{scaleValue(100)};
                margin-left: #{scaleValue(50)};
                padding:  #{scaleValue(20)} 0;

                @media only screen and (max-width: 414px) { 
                    margin-bottom: #{scaleValue(80)};
                    flex-basis: #{scaleValue(600)};
                    height: #{scaleValue(300)};
                    margin-left: #{scaleValue(50)};
                    padding:  #{scaleValue(70)} 0;
                    border-radius: 3rem;
                }
            }

            &--itemhd {
                text-transform: uppercase;
                font-size: #{scaleValue(24)};
                font-weight: 700;

                @media only screen and (max-width: 414px) { 
                    font-size: #{scaleValue(70)};
                }
            }

            &--itemlb {
                font-size: #{scaleValue(20)};
                text-transform: capitalize;
                font-weight: 300;

                @media only screen and (max-width: 414px) { 
                    font-size: #{scaleValue(60)};
                }
            }
        }
    }
</style>