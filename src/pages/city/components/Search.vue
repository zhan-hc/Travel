<template>
  <div class="search">
      <div class="input-wrapper">
        <input v-model="keyword" class="search-input" type="text" placeholder="输入城市名或拼音">
      </div>
      <div class="search-content" ref="searchScroll" v-show="keyword">
        <ul>
          <li class="search-item border-bottom" v-for="item in list" :key="item.id">{{item.name}}</li>
          <li class="search-item border-bottom" v-show="hasNoData">没有找到匹配数据</li>
        </ul>
      </div>
  </div>
</template>

<script type="text/javascript">
import BScroll from 'better-scroll'
export default {
  name: 'CitySearch',
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((value) => {
            if (value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.searchScroll)
  },
  computed: {
    hasNoData () {
      return !this.list.length
    }
  },
  props: {
    cities: Object
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.search
  height .72rem
  padding 0 .1rem
  background $bgColor
  .input-wrapper
    .search-input
      width 100%
      height .62rem
      line-height .62rem
      padding 0 .1rem
      box-sizing border-box
      text-align center
      border-radius .06rem
      color #666
  .search-content
    z-index 1
    overflow hidden
    position absolute
    top 1.58rem
    left 0
    right 0
    bottom 0
    background #eee
    .search-item
      line-height .62rem
      padding-left .2rem
      background #ffffff
      color #666
</style>
