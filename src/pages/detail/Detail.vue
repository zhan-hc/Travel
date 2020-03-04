<template>
  <div class="detail">
      <detail-banner :details='details'></detail-banner>
      <detail-header></detail-header>
      <detail-list :list='details.categoryList'></detail-list>
  </div>
</template>

<script type="text/javascript">
import axios from 'axios'
import DetailBanner from './components/Banner.vue'
import DetailHeader from './components/Header.vue'
import DetailList from './components/List.vue'
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
      axios.get('/api/detail.json', {
        params: {
          id: this.$router.currentRoute.params.id
        }
      }).then(this.getDetailInfoSucc)
    },
    getDetailInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.id = Math.floor(this.$router.currentRoute.params.id) - 1
        this.details = data.hotPlace[this.id]
      }
    }
  },
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  }
}
</script>

<style lang="stylus" scoped >
.detail
  overflow hidden
</style>
