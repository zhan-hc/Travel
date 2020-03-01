<template>
  <div class="alphabet">
      <ul class="list">
          <li class="item" v-for="(item,key) in cities" :key="key">{{key}}</li>
      </ul>
  </div>
</template>

<script type="text/javascript">
export default {
  name: 'CityAlphabet',
  data () {
    return {

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
