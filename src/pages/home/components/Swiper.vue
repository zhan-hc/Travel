<template>
    <div class="wrapper">
    <swiper :options="swiperOption">
        <swiper-slide v-for="swiper in swiperList" :key="swiper.id">
            <img class="swiper-img" :src="swiper.imgUrl"/>
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
    </div>
</template>

<script type="text/javascript">
export default {
  name: 'HomeSwiper',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true // 支持循环
      },
      swiperList: [
        {
          id: '0001',
          imgUrl: 'http://img.zcool.cn/community/01c93b56d7cbc032f875520fde1dfd.jpg@1280w_1l_2o_100sh.jpg'
        },
        {
          id: '0002',
          imgUrl: 'http://img0.imgtn.bdimg.com/it/u=445893612,3717936684&fm=26&gp=0.jpg'
        }]
    }
  }
}
</script>

<style lang="stylus" scoped>
.wrapper >>> .swiper-pagination-bullet-active
    background: #fff
.wrapper
    overflow hidden
    width 100%
    height 0
    padding-bottom 31.25%
    .swiper-img
        width 100%
</style>
