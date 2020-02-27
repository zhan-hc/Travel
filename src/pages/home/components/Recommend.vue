<template>
  <div class="recommend">
      <div class="title-wrapper">
        <img class="title-img" src="https://imgs.qunarzz.com/piao/fusion/1711/16/bfbb9874e8f11402.png">
        <span class="title">本周热门榜单</span>
        <span class="all">全部榜单></span>
      </div>
      <div class="contentwrapper" ref="recScroll">
        <ul class="content" ref="recommend">
            <li class="item" v-for="item in recList" :key="item.id">
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
      recList: [
        {
          id: '0001',
          level: 'https://imgs.qunarzz.com/piao/fusion/1710/ab/159673b63e6ca702.png',
          imgUrl: 'https://imgs.qunarzz.com/sight/p0/2001/a4/a4c44cabe1ef67d9a3.water.jpg_250x250_2c832e7c.jpg',
          title: '世界之窗',
          price: '￥0.4'
        },
        {
          id: '0002',
          level: 'https://imgs.qunarzz.com/piao/fusion/1710/2d/36d0c4adaebbbc02.png',
          imgUrl: 'https://imgs.qunarzz.com/sight/p0/1508/2e/d9363ce50a88c8c5ff5a138c67687cd4.water.jpg_250x250_b592c33d.jpg',
          title: '深圳野生动物园',
          price: '￥1'
        },
        {
          id: '0003',
          level: 'https://imgs.qunarzz.com/piao/fusion/1710/67/edc47ffef9e96b02.png',
          imgUrl: 'https://imgs.qunarzz.com/sight/p0/1912/7c/7c46c8ef2938cd2da3.water.jpg_250x250_24bc542a.jpg',
          title: '东部华侨城大峡谷',
          price: '￥159.6'
        },
        {
          id: '0004',
          imgUrl: 'https://imgs.qunarzz.com/sight/p0/1810/df/df65113c1322333fa3.water.jpg_250x250_cde69668.jpg',
          title: '地王大厦',
          price: '￥60'
        },
        {
          id: '0005',
          imgUrl: 'https://imgs.qunarzz.com/sight/p0/1603/96/96f47768e63ffdbe90.water.jpg_250x250_3f822c64.jpg',
          title: '海上田园',
          price: '￥37'
        },
        {
          id: '0006',
          imgUrl: 'https://imgs.qunarzz.com/sight/p0/1902/6e/6e1aa2596b02031aa3.img.png_250x250_f618efae.png',
          title: '大鹏玫瑰小镇',
          price: '￥26.9'
        }
      ]
    }
  },
  mounted () {
    this._recommedinit()
  },
  methods: {
    _recommedinit () {
      let recWidth = 100 // 图片宽度
      let margin = 5
      let width = (recWidth + margin) * this.recList.length - margin
      this.$refs.recommend.style.width = width + 'px' // 给ul设置了宽度
      this.$nextTick(() => {
        if (!this.recScroll) {
          this.recScroll = new BScroll(this.$refs.recScroll, {
            scrollX: true, // 水平滚动
            eventPassthrough: 'vertical' // 水平滚动时忽略垂直滚动
          })
        } else {
          this.recScroll.refresh()
        }
      })
    }
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
