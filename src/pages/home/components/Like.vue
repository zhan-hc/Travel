<template>
  <div class="like">
      <div class="title-wrapper">
        <img class="title-img" src="https://imgs.qunarzz.com/piao/fusion/1711/89/ebc329f16c55bb02.png">
        <span class="title">猜你喜欢</span>
      </div>
      <ul class="contentwrapper">
          <li class="item border-bottom" v-for="item in weekList" :key="item.id">
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
      weekList: [
        {
          id: '0001',
          imgUrl: 'https://imgs.qunarzz.com/sight/p0/2001/a4/a4c44cabe1ef67d9a3.water.jpg_250x250_2c832e7c.jpg',
          title: '世界之窗',
          seller: '57207',
          price: '￥0.4',
          address: '华侨城',
          desc: '全球微缩景观，精彩演绎娱乐项目应有尽有'
        },
        {
          id: '0002',
          imgUrl: 'https://imgs.qunarzz.com/sight/p0/1508/2e/d9363ce50a88c8c5ff5a138c67687cd4.water.jpg_250x250_b592c33d.jpg',
          title: '深圳野生动物园',
          seller: '24350',
          price: '￥1',
          address: '南山区',
          desc: '帅的人都去过了😎，你还等什么~'
        },
        {
          id: '0003',
          imgUrl: 'https://imgs.qunarzz.com/sight/p0/1912/7c/7c46c8ef2938cd2da3.water.jpg_250x250_24bc542a.jpg',
          title: '东部华侨城大峡谷',
          seller: '10963',
          price: '￥159.6',
          address: '东部华侨城',
          desc: '12月12日11点大侠谷门票12元限量秒杀'
        },
        {
          id: '0004',
          imgUrl: 'https://imgs.qunarzz.com/sight/p0/1810/df/df65113c1322333fa3.water.jpg_250x250_cde69668.jpg',
          title: '地王大厦',
          seller: '5643',
          price: '￥60',
          address: '罗湖区'
        },
        {
          id: '0005',
          imgUrl: 'https://imgs.qunarzz.com/sight/p0/1603/96/96f47768e63ffdbe90.water.jpg_250x250_3f822c64.jpg',
          title: '海上田园',
          seller: '2690',
          price: '￥37',
          address: '宝安区',
          desc: '这里特别受欢迎哟(๑‾ ꇴ ‾๑)'
        },
        {
          id: '0006',
          imgUrl: 'https://imgs.qunarzz.com/sight/p0/1902/6e/6e1aa2596b02031aa3.img.png_250x250_f618efae.png',
          title: '大鹏玫瑰小镇',
          seller: '89',
          price: '￥26.9',
          address: '龙岗区'
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
