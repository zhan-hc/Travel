<template>
  <div class="alphabet">
      <ul class="list">
          <li class="item" v-for="item in letters" :key="item" :ref="item"
          @click="handleLetterClick"
          @touchstart="handleTouchStart"
          @touchmove="handleTouchMove"
          @touchend="handleTouchEnd">{{item}}</li>
      </ul>
  </div>
</template>

<script type="text/javascript">
export default {
  name: 'CityAlphabet',
  data () {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop // A对象距离顶部的距离
  },
  methods: {
    handleLetterClick (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer) // 节流
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY - 79 // 触摸的对象到顶部的距离
          const index = Math.floor((touchY - this.startY) / 20) // 触摸对象的索引
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  props: {
    cities: Object
  }
}
</script>

<style lang="stylus" scoped >
@import '~styles/varibles.styl'
.alphabet
    .list
        display flex
        flex-direction column
        justify-content center
        position absolute
        top 1.58rem
        right 0
        bottom 0
        width .4rem
        .item
            line-height .4rem
            text-align center
            color $bgColor
</style>
