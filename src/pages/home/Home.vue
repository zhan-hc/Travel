<template>
  <div class="home">
    <home-header></home-header>
    <home-swiper :list='swiperList'></home-swiper>
    <home-icons :list='iconList'></home-icons>
    <split></split>
    <home-recommend :list='recList'></home-recommend>
    <split></split>
    <home-like :list='likeList'></home-like>
    <home-weekend :list='weekList'></home-weekend>
  </div>
</template>

<script type="text/javascript">
import axios from 'axios'
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
      // city: '',
      swiperList: [],
      iconList: [],
      recList: [],
      likeList: [],
      weekList: []
    }
  },
  mounted () {
    this.getHomeInfo()
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/index.json').then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        // this.city = data.city
        this.swiperList = data.swiperList
        this.iconList = data.iconList
        this.recList = data.recList
        this.likeList = data.likeList
        this.weekList = data.weekList
      }
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
