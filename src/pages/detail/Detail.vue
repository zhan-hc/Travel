<template>
  <div class="detail">
      <detail-banner :details='details'></detail-banner>
      <detail-header></detail-header>
      <div class="content"></div>
  </div>
</template>

<script type="text/javascript">
import axios from 'axios'
import DetailBanner from './components/Banner.vue'
import DetailHeader from './components/Header.vue'
export default {
  name: 'Detail',
  data () {
    return {
      details: {}
    }
  },
  mounted () {
    this.getDetailInfo()
  },
  methods: {
    getDetailInfo () {
      axios.get('/api/detail.json').then(this.getDetailInfoSucc)
    },
    getDetailInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.details = data
      }
    }
  },
  components: {
    DetailBanner,
    DetailHeader
  }
}
</script>

<style lang="stylus" scoped >
.detail
  .content
    height 50rem
</style>
