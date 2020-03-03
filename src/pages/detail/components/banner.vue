<template>
  <div class="banner">
      <div class="banner-img-wrapper" @click="handleBannerClick">
          <img class="banner-img"
          :src="details.bannerImg">
          <div class="banner-info">
              <div class="title">{{details.sightName}}</div>
              <div class="number">
                <span class="iconfont icon-tupian"></span>
                <span class="imgnum">{{ImgNumbeer}}</span>
              </div>
          </div>
      </div>
      <common-gallary v-show="showGallary" :imgs="details.gallaryImgs" @close="handleBannerClose"></common-gallary>
  </div>
</template>

<script type="text/javascript">
import CommonGallary from 'common/gallary/Gallary.vue'
export default {
  name: 'DetailBanner',
  data () {
    return {
      showGallary: false
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    handleBannerClose () {
      this.showGallary = false
    }
  },
  computed: {
    ImgNumbeer () {
      if (this.details.gallaryImgs) {
        return this.details.gallaryImgs.length
      }
    }
  },
  components: {
    CommonGallary
  },
  props: {
    details: Object
  }
}
</script>

<style lang="stylus" scoped >
.banner
    .banner-img-wrapper
        position relative
        overflow hidden
        height 0
        padding-bottom 55%
        .banner-img
            width 100%
        .banner-info
            display flex
            position absolute
            left 0
            right 0
            bottom 0
            line-height .6rem
            color #fff
            background-image linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,0.8)) // 背景渐变
            .title
                flex 1
                padding .16rem .2rem
                font-size .32rem
            .number
                flex 0 0 .54rem
                height .32rem
                line-height .32rem
                margin-top .32rem
                margin-right .24rem
                padding 0 .32rem
                border-radius .2rem
                font-size .24rem
                background rgba(0,0,0,0.4)
                .icon-tupian
                    font-size .24rem
</style>
