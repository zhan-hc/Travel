<template>
  <div class="weekend">
      <div class="title-wrapper">
        <span class="title">周末去哪里</span>
      </div>
      <ul class="contentwrapper">
          <li class="item border-bottom" v-for="item in weekList" :key="item.id">
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
      weekList: [
        {
          id: '0001',
          imgUrl: 'https://imgs.qunarzz.com/sight/source/1507/d9/2ddc7652fdba16.jpg_r_640x214_5e62f1a3.jpg',
          title: '深圳周边游',
          desc: '远离城市拥堵，去周边开启清新假期吧。'
        },
        {
          id: '0002',
          imgUrl: 'https://imgs.qunarzz.com/sight/source/1811/15/66f14e0fd6fbb.jpg_r_640x214_5d69f21d.jpg',
          title: '清远周边逛',
          desc: '人人都有一双发现美的眼睛，身边的事物最熟悉不过，那你可曾发现了被人遗漏的美？'
        },
        {
          id: '0003',
          imgUrl: 'https://imgs.qunarzz.com/sight/source/1811/b8/5d599bbdcf8b57.jpg_r_640x214_2ee055e3.jpg',
          title: '浮在海上的绿洲',
          desc: '南国滨海之城，避寒胜地，有暖暖的阳光，海风习习，吃着海鲜逛逛老街多惬意啊'
        },
        {
          id: '0004',
          imgUrl: 'https://imgs.qunarzz.com/sight/source/1505/fa/ca65fde9677de2.jpg_r_640x214_4500e3ff.jpg',
          title: '深圳必打卡',
          desc: '来到深圳，你需要来这里签到'
        }
      ]
    }
  },
  components: {
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
                padding-bottom 33.9%
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
