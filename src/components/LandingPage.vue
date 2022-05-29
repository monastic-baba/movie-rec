<template>
  <div class="landing-page">
    <Header />
    <Banner />
    <Recommender />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Header from "./Header.vue";
import Banner from "./Banner.vue";
import Recommender from "./Recommender.vue";

@Component({
  components: {
    Header,
    Banner,
    Recommender,
  },
})
export default class LandingPage extends Vue {}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.landing-page {
  background: linear-gradient(270deg, #87c5ff 0%, #00274b 100%, #00274b 100%);
  background-blend-mode: darken;
  height: 150vh;
}
</style>
