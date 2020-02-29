<template>
  <div class="recommend">
      <div class="title-wrapper">
        <img class="title-img" src="https://imgs.qunarzz.com/piao/fusion/1711/16/bfbb9874e8f11402.png">
        <span class="title">本周热门榜单</span>
        <span class="all">全部榜单></span>
      </div>
      <div class="contentwrapper" ref="recScroll">
        <ul class="content" ref="recommend">
            <li class="item" v-for="item in list" :key="item.id">
                <img class="level" v-show="item.level" :src="item.level">
                <img class="item-img" :src="item.imgUrl">
                <div class="item-info">
                    <p class="title">{{item.title}}</p>
                    <p class="price"><span>{{item.price}}</span>起</p>
                </div>
            </li>
        </ul>
      </div>
  </div>
</template>

<script type="text/javascript">
import BScroll from 'better-scroll'
export default {
  name: 'HomeRecommend',
  data () {
    return {
    }
  },
  watch: {
    list (newValue, oldValue) {
      this._recommedinit()
    }
  },
  methods: {
    _recommedinit () {
      let recWidth = 100 // 图片宽度
      let margin = 5
      let width = (recWidth + margin) * this.list.length - margin
      this.$refs.recommend.style.width = width + 'px' // 给ul设置了宽度
      // this.$nextTick(() => {
      if (!this.recScroll) {
        this.recScroll = new BScroll(this.$refs.recScroll, {
          scrollX: true, // 水平滚动
          eventPassthrough: 'vertical' // 水平滚动时忽略垂直滚动
        })
      } else {
        this.recScroll.refresh()
      }
      // })
    }
  },
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
.recommend
    .title-wrapper
        position relative
        .title-img
            width .3rem
            height .3rem
            margin-top -.2rem
        .title
            margin-top .2rem
            line-height .8rem
            text-indent .2rem
        .all
            position absolute
            bottom .2rem
            right .2rem
            font-size .24rem
            color rgba(7,17,27,0.8)
    .contentwrapper
      width 100%
      overflow hidden
      white-space nowrap
      .content
          position relative
          padding .2rem
          .item
              display inline-block
              width 2rem
              margin-right .2rem
              .level
                  position relative
                  display block
                  top -.1rem
                  left -.1rem
                  width .8rem
                  height .4rem
                  vertical-align top
              .item-img
                  display block
                  margin-top -.4rem
                  width 2rem
                  height 2rem
              .item-info
                  text-align center
                  font-size .24rem
                  .title
                      margin-top .1rem
                  .price
                      margin-top .1rem
                      span
                          color #FFA500

</style>
