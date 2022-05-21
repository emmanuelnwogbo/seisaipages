<template>
    <div>
        <div class="pagetwo">
            <div class="pagetwo__base">
                <figure class="pagetwo__base--img">
                    <img src="@/assets/imgs/walltwo.svg" />
                </figure>
                <div class="pagetwo__base--body">
                    <div class="pagetwo__base--card">
                        <div class="pagetwo__base--cardtop">
                            <span></span>
                            <!---<span @click="$router.push('/')">
                                <figure>
                                    <img src="@/assets/imgs/x.svg" />
                                </figure>
                            </span>-->
                        </div>
                        <div class="pagetwo__base--cardsentence">
                            <p>Are you ready to take the pill?</p>
                        </div>
                        <div class="pagetwo__base--cardbtns">
                            <span @click="$router.replace('/folders')">Yes</span>
                            <span @click="$router.replace('/folders')">Definitely</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {

    }
</script>

<style lang="scss" scoped>
@function scaleValue($value) {
    @return calc(
      #{$value} * (clamp(350px, 100vw, 3840px) / var(--ideal-viewport-width))
    );
}


    .pagetwo {
        height: 100vh;

        &__base {
            position: relative;
            color: #000000;

            &--img {
                position: fixed;
                top: 0;
                left: 0;
                width: 100vw;

                @media only screen and (max-width: 414px) { 
                    height: #{scaleValue(3390)};
                }

                & img {
                    object-fit: cover;
                    height: 100%;
                    width: 100%;
                }
            }

            &--body {
                position: fixed;
                top: 0;
                left: 0;
                height: 100vh;
                width: 100vw;
                z-index: 1;
                display: flex;
                align-items: center;
                justify-content: center;
            }

            &--card {
                width:  #{scaleValue(660)};
                height:  #{scaleValue(284)};
                background: rgba(196, 196, 196, 1);
                text-align: center;
                font-size: #{scaleValue(24)};

                @media only screen and (max-width: 414px) { 
                    width:  #{scaleValue(1400)};
                    height:  #{scaleValue(700)};
                }
            } 

            &--cardtop {
                height:  #{scaleValue(50)};
                background: #000000;
                margin-bottom:  #{scaleValue(50)};
                display: flex;
                justify-content: space-between;
                padding: #{scaleValue(10)};
                align-items: center;

                @media only screen and (max-width: 414px) { 
                    height:  #{scaleValue(200)};
                }

                & span {
                    
                    &:nth-child(2) {
                        display: inline-block;
                        background: rgba(196, 196, 196, 1);
                        padding: 0 #{scaleValue(10)};
                        cursor: pointer;
                    }
                }

                & figure {
                    width:  #{scaleValue(15)};

                    & img {
                        object-fit: cover;
                        height: 100%;
                        width: 100%;
                    }
                }
            } 

            &--cardsentence {
                margin-bottom:  #{scaleValue(50)};

                @media only screen and (max-width: 414px) { 
                    font-size:  #{scaleValue(85)};
                }
            }

            &--cardbtns {
                display: flex;
                justify-content: space-between;
                padding: 0 #{scaleValue(140)};

                & span {
                    display: inline-block;
                    border: 3px solid #000000;
                    padding: #{scaleValue(10)} 0;
                    cursor: pointer;
                    font-size: #{scaleValue(20)};
                    width: #{scaleValue(170)};
                    text-align: center;

                    @media only screen and (max-width: 414px) { 
                        font-size:  #{scaleValue(80)};
                        width: #{scaleValue(520)};
                        height: #{scaleValue(190)};
                        display: flex;
                        justify-content: center;
                        align-items: center;
                    }
                }
            }
        }
    }
</style>