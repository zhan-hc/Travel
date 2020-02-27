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
      iconList: [
        {
          id: '0001',
          imgUrl: 'https://imgs.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
          desc: '景点门票'
        },
        {
          id: '0002',
          imgUrl: 'https://imgs.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png',
          desc: '深圳必游'
        },
        {
          id: '0003',
          imgUrl: 'https://imgs.qunarzz.com/piao/fusion/1803/4d/a1eda1a2b8414302.png',
          desc: '夜场狂欢'
        },
        {
          id: '0004',
          imgUrl: 'https://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/815c90e59498644296e340c815e1269a.png',
          desc: '世界之窗'
        },
        {
          id: '0005',
          imgUrl: 'https://imgs.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png',
          desc: '一日游'
        },
        {
          id: '0006',
          imgUrl: 'https://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20194/cba147cf6cfcea7109d0bff6aac6f626.png',
          desc: '深圳动物园'
        },
        {
          id: '0007',
          imgUrl: 'https://imgs.qunarzz.com/piao/fusion/1803/ab/6f7d6e44963c9302.png',
          desc: '泡温泉'
        },
        {
          id: '0008',
          imgUrl: 'https://imgs.qunarzz.com/piao/fusion/1803/b6/37560ece9c62b502.png',
          desc: '东部华侨城'
        },
        {
          id: '0009',
          imgUrl: 'https://imgs.qunarzz.com/piao/fusion/1803/b6/37560ece9c62b502.png',
          desc: '高空观景'
        },
        {
          id: '0010',
          imgUrl: 'https://imgs.qunarzz.com/piao/fusion/1803/b1/528a9e80403b8c02.png',
          desc: '玩转长隆'
        }
      ],
      swiperOption: {
        pagination: '.swiper-pagination'
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconList.forEach((item, index) => {
        const page = Math.floor(index / 8) // icon处在第几页
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
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
