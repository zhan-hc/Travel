<template>
  <div class="detail-list">
    <div class="list-info border-bottom">
          <div class="grade border-right">
              <div class="score"><span>{{lists.score}}</span>分 {{lists.desc}}</div>
              <div class="seller">{{lists.seller}}条评论 {{lists.strategy}}条攻略</div>
              <div class="iconfont icon-right"></div>
          </div>
          <div class="desc">
              <div class="title">景点简介</div>
              <div class="text">开放时间、贴士</div>
              <div class="iconfont icon-right"></div>
          </div>
    </div>
    <div class="list-address border-bottom">
        <span class="iconfont icon-address"></span>
        {{lists.address}}
        <span class="iconfont icon-right"></span>
    </div>
    <split></split>
    <div class="list-day">
        <div class="title border-bottom">
            <div class="icon"></div>{{lists.type}}
        </div>
        <div class="item border-bottom" v-for="(item, index) in tour" :key="index">
            <div class="text">{{item.text}}</div>
            <div class="price-wrapper">
              <div class="price">￥<span>{{item.price}}</span></div>起
            </div>
            <div class="iconfont icon-bottom"></div>
        </div>
        <div class="develop" v-show="showDevelop" @click="handleDevelop">
            查看剩余产品<span class="iconfont icon-bottom"></span>
        </div>
    </div>
    <split></split>
    <div class="list-assess">
      <div class="title border-bottom">
        <span class="iconfont icon-I"></span>用户评论
      </div>
      <div class="content-wrapper border-bottom">
        <div class="content border-bottom" v-for="item in lists.assess" :key="item.id">
          <div class="left">
            <span v-for="i in 5" :key="i" class="iconfont icon-xing"></span>
          </div>
          <div class="right">
            <div class="username">{{item.username}}</div>
            <div class="time">{{item.time}}</div>
          </div>
          <div class="main">
            <div class="text">{{item.text}}</div>
          </div>
          <div class="img-wrapper" v-show="item.img">
            <div class="list-img" v-for="(imgs, index) in item.img" :key="index">
              <img :src="imgs">
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">
import split from 'common/split/split.vue'
export default {
  name: 'DetailList',
  data () {
    return {
      lists: [],
      tour: [],
      limit: 0,
      showDevelop: true
    }
  },
  components: {
    split
  },
  watch: {
    list () {
      this.lists = this.list[0]
      this.limit = this.lists.daytour.length
      if (this.limit > 2) {
        this.tour = this.lists.daytour.slice(0, 2)
      } else {
        this.tour = this.lists.daytour
        this.showDevelop = false
      }
    }
  },
  methods: {
    handleDevelop () { // 点击展开
      this.showDevelop = false
      let num = this.lists.daytour.length
      this.tour = this.lists.daytour.slice(0, num)
    }
  },
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped >
@import '~styles/mixins.styl'
.detail-list
    .list-info
            display flex
            border-radius .2rem
            .grade
                flex 1
                position relative
                padding .2rem
                .score
                    color #ffa500
                    span
                        font-size .42rem
                .seller
                    color #999
                    font-size .24rem
                    padding-top .1rem
                .icon-right
                    position absolute
                    right .2rem
                    bottom .4rem
            .desc
                flex 1
                position relative
                padding .2rem
                .title
                    padding-top .1rem
                .text
                    color #999
                    font-size .24rem
                    padding-top .1rem
                .icon-right
                    position absolute
                    right .2rem
                    bottom .4rem
    .list-address
        position: relative
        padding: .2rem .56rem
       .icon-address
            display: block
            height: 100%
            line-height: 100%
            position: absolute
            padding-left .2rem
            left: 0
        .icon-right
                position: absolute
                right: .2rem
                top: 50%
                margin-top: -.14rem
                color: #9e9e9e
                font-size: .24rem
    .list-day
        .title
            line-height .8rem
            font-size .32rem
            padding 0 .2rem
            .icon
                position relative
                display: inline-block
                left .06rem
                top .06rem
                width: .36rem
                height: .36rem
                background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat
                margin-right: .1rem
                background-size: .4rem 3rem
        .item
            position relative
            padding .2rem
            z-index: 2
            .text
                overflow:hidden
                text-overflow:ellipsis
                display:-webkit-box
                -webkit-box-orient:vertical
                -webkit-line-clamp:2
                padding-right .1rem
                margin-right: 1.8rem
                font-size: .3rem
                line-height: .48rem
            .price-wrapper
                overflow: hidden
                position: absolute
                top: 50%
                right: .46rem;
                margin-top: -.28rem
                font-size: .24rem
                height: .4rem
                line-height: .4rem
                font-size .22rem
                padding-right .1rem
                .price
                    display inline-block
                    color #ffa500
                    span
                        font-size .38rem
            .icon-bottom
                overflow: hidden
                position: absolute
                top: 50%
                height: .4rem
                line-height: .4rem
                right: .2rem
                margin-top: -.22rem
                color: #bbb
                font-size: .24rem
        .develop
            text-align center
            padding .3rem
            .icon-bottom
                font-size .2rem
    .list-assess
      .title
        padding .32rem
        font-size .32rem
        .icon-I
          color #1ba9ba
      .content-wrapper
        .content
          position relative
          padding .32rem
          .left
            .icon-xing
              font-size .20rem
              color #ffa500
              margin-right .02rem
          .right
            position absolute
            right .3rem
            top .3rem
            .username
              display inline-block
            .time
              display inline-block
          .main
            .text
              // ellipsis-row(5)
              padding-top .2rem
              line-height .44rem
          .img-wrapper
            position relative
            .list-img
              display inline
              margin-left: .07rem
              img
                width: 31%
                margin-bottom: .15rem
                background-size: contain

</style>
