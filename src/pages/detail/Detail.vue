<template>
  <div>
    <detail-banner :sightName="sightName" :gallaryImgs="gallaryImgs" :bannerImg="bannerImg"></detail-banner>
    <detail-header></detail-header>
    <div class="content"></div>
  </div>
</template>

<script>
import axios from 'axios'
import DetailBanner from './components/banner'
import DetailHeader from './components/header'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader
  },
  data () {
    return {
      sightName: '',
      bannerImg: String,
      gallaryImgs: [],
      categoryList: {}
    }
  },
  methods: {
    getDetail () {
      axios.get('api/detail.json')
        .then(this.applyDetailInfo)
    },
    applyDetailInfo (res) {
      res = res.data
      if (res.ret && res.data) {
        let data = res.data
        this.sightName = data.sightName
        console.log(this.sightName)
        this.bannerImg = data.bannerImg
        this.gallaryImgs = data.gallaryImgs
        this.categoryList = data.categoryList
      }
    }
  },
  mounted () {
    this.getDetail()
  }
}
</script>

<style lang="stylus" scoped>
  .content
    height 2000px
    background-color #666
</style>
