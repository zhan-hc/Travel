<template>
  <div class="weekend">
      <div class="title-wrapper">
        <span class="title">周末去哪里</span>
      </div>
      <ul class="contentwrapper">
          <li class="item border-bottom" v-for="item in list" :key="item.id">
              <div class="item-img-wrapper">
                <img class="item-img" :src="item.imgUrl">
              </div>
              <div class="info">
                  <p class="title">{{item.title}}</p>
                  <div class="desc" v-show="item.desc"><span>{{item.desc}}</span></div>
              </div>
          </li>
      </ul>
  </div>
</template>

<script type="text/javascript">
export default {
  name: 'HomeWeekend',
  data () {
    return {
    }
  },
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.weekend
    .title-wrapper
        position relative
        background #f5f5f5
        .title
            display block
            margin-top .2rem
            line-height .8rem
            text-indent .2rem
    .contentwrapper
        .item
            .item-img-wrapper
                overflow hidden
                height 0
                padding-bottom 37.09%
                .item-img
                    width 100%
            .info
                padding .1rem
                .title
                    line-height .54rem
                    font-size .32rem
                    ellipsis()
                .desc
                    margin-right: .24rem
                    padding: .04rem .1rem
                    font-size: .24rem
                    line-height: .34rem
                    overflow: hidden
                    white-space: nowrap
                    text-overflow: ellipsis
                    margin-bottom .2rem
</style>
