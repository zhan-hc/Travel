<template>
  <div class="home">
    <home-header></home-header>
    <home-swiper></home-swiper>
    <home-icons></home-icons>
    <split></split>
    <home-recommend></home-recommend>
    <split></split>
    <home-like></home-like>
    <home-weekend></home-weekend>
  </div>
</template>

<script type="text/javascript">
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import split from '../home/split'
import HomeLike from '../home/components/Like'
import HomeWeekend from '../home/components/Weekend'
export default {
  name: 'Home',
  data () {
    return {
    }
  },
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    split,
    HomeLike,
    HomeWeekend
  }
}
</script>

<style lang="stylus" scoped ref="stylesheet/stylus">
</style>
