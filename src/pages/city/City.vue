<template>
  <div class="city">
    <city-header></city-header>
    <city-search></city-search>
  </div>
</template>

<script type="text/javascript">
import CityHeader from './components/Header'
import CitySearch from './components/Search'
export default {
  name: 'city',
  data () {
    return {

    }
  },
  components: {
    CityHeader,
    CitySearch
  }
}
</script>

<style lang="stylus" scoped>
</style>
