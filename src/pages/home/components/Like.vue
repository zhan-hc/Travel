<template>
  <div class="like">
      <div class="title-wrapper">
        <img class="title-img" src="https://imgs.qunarzz.com/piao/fusion/1711/89/ebc329f16c55bb02.png">
        <span class="title">猜你喜欢</span>
      </div>
      <ul class="contentwrapper">
          <li class="item border-bottom" v-for="item in list" :key="item.id">
                <img class="item-img" :src="item.imgUrl">
              <div class="info">
                  <p class="title">{{item.title}}</p>
                  <p class="assess">⭐⭐⭐⭐⭐{{item.seller}}条评论</p>
                  <div class="basic">
                    <div class="price"><span>{{item.price}}</span>起</div>
                    <div class="address">{{item.address}}</div>
                  </div>
                  <div class="desc" v-show="item.desc"><span>{{item.desc}}</span></div>
              </div>
          </li>
      </ul>
  </div>
</template>

<script type="text/javascript">
export default {
  name: 'HomeLike',
  data () {
    return {
    }
  },
  components: {
  },
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.like
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
    .contentwrapper
        .item
            overflow hidden
            display flex
            height 1.9rem
            .item-img
                width 1.7rem
                height 1.7rem
                padding .1rem
            .info
                flex 1
                padding .1rem
                .title
                    line-height .54rem
                    font-size .32rem
                .assess
                    line-height .4rem
                    font-size .24rem
                .basic
                    .price
                        display inline
                        margin-top .1rem
                        width 50%
                        font-size .24rem
                        span
                            color #FFA500
                            font-size .4rem
                    .address
                        display inline
                        margin-right .24rem
                        float right
                        font-size .24rem
                        ellipsis()
                .desc
                    display: inline-block
                    // margin-top: .48rem
                    margin-right: .24rem
                    background: #fff9f9
                    padding: .04rem .1rem
                    color: #f55
                    font-size: .24rem
                    line-height: .34rem
</style>
