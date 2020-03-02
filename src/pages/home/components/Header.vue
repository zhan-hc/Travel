<template>
  <div class="header">
    <div class="header-left">
        <div class="iconfont back-icon">&#xe624;</div>
    </div>
    <div class="header-input">
        <span class="iconfont">&#xe632;</span>
        输入城市/游玩/景点主题
        </div>
    <router-link to="/city">
      <div class="header-right">
          {{city}}
          <span class="iconfont arrow-icon">&#xe64a;</span>
      </div>
    </router-link>
  </div>
</template>

<script type="text/javascript">
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  data () {
    return {
    }
  },
  computed: {
    ...mapState(['city'])
  },
  props: {
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
@import '~styles/mixins.styl'
    .header
        display flex
        height $headerHeight
        line-height $headerHeight
        background $bgColor
        color #fff
        .header-left
            width .64rem
            float left
            .back-icon
                text-align center
                font-size .4rem
        .header-input
            flex 1
            height .64rem
            line-height .64rem
            margin-top .12rem
            margin-left .2rem
            padding-left .2rem
            background #fff
            border-radius .1rem
            color #ccc
        .header-right
            min-width 1.04rem
            padding 0 .1rem
            float left
            text-align center
            color #fff
            // ellipsis()
            .arrow-icon
                margin-left -.04rem
                font-size .24rem
</style>
