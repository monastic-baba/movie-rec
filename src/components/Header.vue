<template>
  <div class="header">
    <div class="header__left">
      <div class="header__title">MOVIEMANIA</div>
      <img
        class="header__icon"
        src="../assets/video-player.png"
        height="65"
        width="65"
        alt=""
      />
    </div>
    <div class="header__right">
      <div class="header__button">Logout</div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class Header extends Vue {}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.header {
  display: flex;
  align-content: center;
  justify-content: space-between;
  padding: 15px;
  background: linear-gradient(270deg, #8794a1 0%, #202f3d 100%, #17212b 100%);
  background-blend-mode: darken;
  &__left {
    display: flex;
    justify-content: space-between;
    padding-top: 5px;
  }
  &__title {
    font-weight: 500;
    font-size: 16px;
    color: white;
  }
  &__icon {
    height: 20px;
    width: 20px;
    margin-left: 10px;
  }
  &__button {
    background: rgba(179, 47, 47, 0.9);
    border-radius: 50px;
    color: white;
    font-size: 10px;
    font-weight: 700;
    padding: 8px;
  }
}
</style>
