<template>
  <div class="city">
    <city-header></city-header>
    <city-search></city-search>
    <city-list></city-list>
    <city-alphapet></city-alphapet>
  </div>
</template>

<script type="text/javascript">
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphapet from './components/Alphapet'
export default {
  name: 'city',
  data () {
    return {

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
