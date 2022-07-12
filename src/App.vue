<template>
  <div id="app">

    <AmHeader @toSearch="SearchText"/>
    
    <AmMain :filmlist="filmList"/>

  </div>
</template>

<script>
import AmHeader from "./components/AmHeader.vue";
import  AmMain  from "./components/AmMain.vue";
import axios from 'axios';

export default {
  name: 'App',
  components: {
    AmHeader,
    AmMain
  },

  data() {
    return {
      url:"https://api.themoviedb.org/3/search/movie?api_key=46cb34a5ad0781124c39c2a133f7475b&language=en-US",
      filmList: []
    }
  },
  methods: {
  getFilmApi(userText) {
    axios.get(`${this.url}&query=${userText}`)
    .then((response) => {
      this.filmList = response.data.results;
    });
  },

  SearchText(userText) {
    this.getFilmApi(userText);
    }
  },
  
}
</script>

<style lang="scss">
@import './assets/style/common.scss';

</style>