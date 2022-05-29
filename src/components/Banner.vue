<template>
  <div class="banner">
    <div class="banner__left">
      <div class="banner__text">
        Get your daily dose <br />
        of movie, <span class="banner__text--highlight">for free</span> !
      </div>
      <div class="banner__button">Start Now</div>
    </div>
    <div class="banner__right">
      <div>
        <img class="banner__image" src="../assets/film-reel.png" alt="" />
        <img class="banner__image" src="../assets/popcorn.png" alt="" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class Banner extends Vue {}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.banner {
  width: 100%;
  display: flex;
  justify-content: center;
  &__image {
    height: 150px;
    width: 100px;
    margin-top: 50px;
  }
  &__left {
    padding: 5%;
  }
  &__text {
    font-weight: 700;
    font-size: 30px;
    color: #ffffff;
    text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    &--highlight {
      text-transform: uppercase;
      color: tomato;
    }
  }
  &__button {
    background: rgba(179, 47, 47, 0.9);
    border-radius: 50px;
    color: white;
    font-size: 18px;
    font-weight: 700;
    padding: 8px;
    margin-top: 12px;
  }
}
</style>
