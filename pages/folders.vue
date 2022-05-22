<template>
  <div>
    <div class="entrance">
      <header class="entrance__header">
        <figure class="entrance__header--logo">
          <img src="@/assets/imgs/logo.svg" />
        </figure>
      </header>
      <figure class="entrance__base">
        <img src="@/assets/imgs/wall.svg"/>
     </figure>
     <div class="entrance__folders">
        <div class="entrance__folder" @click="$router.push('/pill')">
          <figure class="entrance__folder--fig">
            <img src="@/assets/imgs/folder.svg"/>
          </figure>
          <div class="entrance__folder--label">
            <p>The pill</p>
          </div>
        </div>
        <div class="entrance__folder" @click="openmintpage">
          <figure class="entrance__folder--fig">
            <img src="@/assets/imgs/folder.svg"/>
          </figure>
          <div class="entrance__folder--label">
            <p>Mint</p>
          </div>
        </div>
        <div class="entrance__folder blured">
          <figure class="entrance__folder--fig">
            <img src="@/assets/imgs/folder.svg"/>
          </figure>
          <div class="entrance__folder--label">
            <p>Gallery</p>
          </div>
        </div>
        <div class="entrance__folder blured">
          <figure class="entrance__folder--fig">
            <img src="@/assets/imgs/folder.svg"/>
          </figure>
          <div class="entrance__folder--label">
            <p>The map</p>
          </div>
        </div>
     </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  methods: {
    openmintpage() {
      window.open('https://mint.saisei.art/');
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

  .entrance {
    color: #fff;
    font-size: #{scaleValue(30)};

    &__header {
      position: fixed;
      top: 0;
      left: 0;
      z-index: 1;
      width: 100vw;
      display: flex;
      justify-content: space-between;

      &--logo {
        cursor: pointer;
      }
    }

    &__base {
      position: fixed;
      height: 100vh;
      width: 100vw;
      top: 0;
      left: 0;

      & img {
        object-fit: cover;
        height: 100%;
        width: 100%;
      }
    }

    &__folders {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      z-index: 2;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;

      @media only screen and (max-width: 414px) { 
          top: #{scaleValue(500)};
          height: 62vh;
      }
    }

    &__folder {
      flex-basis: #{scaleValue(600)};
      display: flex;
      align-items: center;
      justify-content: center;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      flex-direction: column;

      @media only screen and (max-width: 414px) { 
          
          & figure {

            & img {
              width: #{scaleValue(400)};
            }
          }
      }

      &--label {
        text-align: left;

        @media only screen and (max-width: 414px) { 
            font-size: #{scaleValue(80)};
        }
      }
    }
  }

  .blured {
    opacity: .3;
    cursor: progress;
  }
</style>
