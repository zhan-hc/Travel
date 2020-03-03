<template>
  <div class="header">
      <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
        <span class="iconfont icon-fanhui"></span>
      </router-link>
      <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
          景点详情
      <router-link to="/">
        <span class="iconfont icon-fanhui"></span>
      </router-link>
      </div>
  </div>
</template>

<script type="text/javascript">
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll) // 页面展示时绑定scroll事件
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll) // 页面消失时解绑scroll事件
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 50) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity // 当滑动高度超过140时透明度变成1，否则就是一个渐变的效果
        this.opacityStyle = {opacity}
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  }
}
</script>

<style lang="stylus" scoped >
@import '~styles/varibles.styl'
.header
    .header-abs
        position absolute
        left .2rem
        top .2rem
        width .8rem
        height .8rem
        line-height .8rem
        border-radius .4rem
        text-align center
        background rgba(0,0,0,.8)
        font-size .4rem
        color #fff
    .header-fixed
        position fixed
        top 0
        left 0
        right 0
        overflow hidden
        height $headerHeight
        line-height $headerHeight
        text-align center
        color #ffffff
        background $bgColor
        font-size .32rem
        .icon-fanhui
            position absolute
            top 0
            left 0
            width .64rem
            text-align center
            font-size .4rem
            color #fff
</style>
