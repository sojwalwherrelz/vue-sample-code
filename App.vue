<template>
  <!-- <CountriesApi msg="Welcome to Your Vue.js App"/> -->
  <!-- <MatchList msg="Welcome to Your Vue.js App"/> -->
  <!-- <MatchList msg="Welcome to Your Vue.js App"/> -->
  <!-- <PlayersInfo msg="Welcome to Your Vue.js App"/> -->
  <!-- <SeriesInfo msg="Welcome to Your Vue.js App"/> -->
  <MatchInfo/>

</template>

<script>
// import CountriesApi from './components/CountriesApi.vue'
// import MatchList from './components/MatchList.vue'
// import Players from './components/Players.vue'
// import PlayersInfo from './components/PlayersInfo.vue'
// import SeriesInfo from './components/SeriesInfo.vue'
import MatchInfo from './components/MatchInfo.vue'

export default {
  name: 'App',
  components: {
    // CountriesApi,
    // MatchList,
    // Players,
    // PlayersInfo,
    // SeriesInfo,
    MatchInfo,

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
