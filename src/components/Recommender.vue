<template>
  <div class="recommender">
    <div v-if="loading" class="loader"></div>
    <div class="field">
      <div class="field__label">Enter a search string :</div>
      <input class="field__input" v-model="userInput" />
    </div>
    <div class="field">
      <div class="field__label">
        Enter number of movies to display which are similar to movie name
        closest to search string :
      </div>
      <input class="field__input" v-model="n" />
    </div>
    <button class="recommender__cta" @click="getRecommendations">
      Get Recommendations
    </button>
    <div v-for="(movie, index) in recommendations" :key="index">
      <div class="recommendation">
        <div>{{ index + 1 }}</div>
        <div>
          <b>{{ getMovieNameFromTitle(movie) }}</b>
        </div>
        <div>{{ getMovieYearFromTitle(movie) }}</div>
      </div>
    </div>
    <div v-if="recommendations.length == 0" class="recommender__cta">
      NO MOVIES TO SHOW
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import axios from "axios";
import { Input } from "vuesax";

@Component({
  components: {
    Input,
  },
})
export default class Recommender extends Vue {
  private userInput = "";
  private n = 3;
  private loading = false;
  private recommendations: string[] = [];
  private recommendations2 = [
    "The Fault in Our Stars (2014)",
    "Lucy (2014)",
    "X-Men: Days of Future Past (2014)",
    "Maleficent (2014)",
    "Home (2015)",
    "Strange Love of Martha Ivers, The (1946)",
    "Once a Thief (Zong heng si hai) (1991)",
    "More American Graffiti (1979)",
  ];

  private getRecommendations() {
    this.loading = true;
    axios
      .get(
        `https://piplup-mew.herokuapp.com/movie/${this.userInput}?count=${this.n}`
      )
      .then((res: any) => {
        console.log(res);
        this.recommendations = res.data.data;
        this.loading = false;
      })
      .catch(() => {
        this.loading = false;
      });
  }

  getMovieYearFromTitle(movie: string) {
    let str = movie.slice(movie.length - 5);
    return str.slice(0, str.length - 1);
  }

  getMovieNameFromTitle(movie: string) {
    return movie.slice(0, movie.length - 6);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.recommender {
  .field {
    display: flex;
    justify-content: space-between;
    font-weight: 600;
    color: white;
    padding: 0px 200px;
    &__label {
      align-self: center;
    }
    &__input {
      border-radius: 12px;
      margin: 5px;
      line-height: 26px;
      text-align-last: center;
    }
  }
  .recommendation {
    display: flex;
    justify-content: space-between;
    border-radius: 50px;
    background: #00274b;
    width: 350px;
    padding: 10px 30px;
    margin: 5px auto;
    opacity: 0.5;
    color: white;
  }
  &__cta {
    background: rgba(179, 47, 47, 0.9);
    border-radius: 50px;
    color: white;
    font-size: 10px;
    font-weight: 700;
    padding: 15px;
    margin: 40px 0px;
  }
  .loader {
    border: 16px solid #f3f3f3;
    border-radius: 50%;
    border-top: 16px solid #3498db;
    width: 120px;
    height: 120px;
    margin: auto;
    -webkit-animation: spin 2s linear infinite; /* Safari */
    animation: spin 2s linear infinite;
  }

  /* Safari */
  @-webkit-keyframes spin {
    0% {
      -webkit-transform: rotate(0deg);
    }
    100% {
      -webkit-transform: rotate(360deg);
    }
  }

  @keyframes spin {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
}
</style>
