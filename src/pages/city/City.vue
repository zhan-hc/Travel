<template>
  <div class="city">
    <city-header></city-header>
    <city-search></city-search>
    <city-list :cities="cities" :hot="hotCities" :letter="letter"></city-list>
    <city-alphapet :cities="cities" @change="handleLetterChange"></city-alphapet>
  </div>
</template>

<script type="text/javascript">
import axios from 'axios'
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphapet from './components/Alphapet'
export default {
  name: 'city',
  data () {
    return {
      cities: {},
      hotCities: [],
      letter: ''
    }
  },
  mounted () {
    this.getCityInfo()
  },
  methods: {
    getCityInfo () {
      axios.get('/api/city.json').then(this.handleGetCityInfoSucc)
    },
    handleGetCityInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.cities = data.cities
        this.hotCities = data.hotCities
      }
    },
    handleLetterChange (letter) {
      this.letter = letter
    }
  },
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphapet
  }
}
</script>

<style lang="stylus" scoped>
</style>
