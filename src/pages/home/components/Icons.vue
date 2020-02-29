<template>
  <div class="icons">
    <swiper :options="swiperOption">
        <swiper-slide v-for="(page, index) in pages" :key="index">
            <div class="icon" v-for="icon in page" :key="icon.id">
                <div class="icon-img">
                    <img class="icon-img-content" :src="icon.imgUrl"/>
                </div>
                <p class="icon-desc">{{icon.desc}}</p>
            </div>
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script type="text/javascript">
export default {
  name: 'HomeIcons',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        autoplay: false // 取消循环
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8) // icon处在第几页
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  },
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
@import '~styles/mixins.styl'
.icons >>> .swiper-container
    height 0
    padding-bottom 50%
.icons
  .icon
      position relative
      overflow hidden
      float left
      width 25%
      height 0
      padding-bottom 22%
      .icon-img
          position absolute
          top 0
          left 0
          right 0
          bottom .44rem
          box-sizing border-box
          padding .1rem
          .icon-img-content
              display block
              margin 0 auto
              height 100%
      .icon-desc
          position absolute
          left 0
          right 0
          bottom 0
          height .44rem
          line-height .44rem
          text-align center
          color $darkTextColor
          ellipsis()

</style>
