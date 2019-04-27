<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" :src="bannerImg" alt="">
      <div class="banner-info">
        <div class="banner-title">{{this.sightName}}</div>
        <div class="banner-num"><span class="iconfont">&#xe7e1;</span>&nbsp;39</div>
      </div>
    </div>
    <common-gallary :gallaryImgs="gallaryImgs" v-show="this.$store.state.showGallary" @close="handleGallaryClose"></common-gallary>
  </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
export default {
  name: 'DetailBanner',
  data () {
    return {
    }
  },
  components: {
    CommonGallary
  },
  props: {
    bannerImg: {} ,
    sightName: {
      type: String
    },
    gallaryImgs: {
      type: Array
    }
  },
  methods: {
    handleBannerClick () {
      this.$store.state.showGallary = true
    },
    handleGallaryClose () {
      this.$store.state.showGallary = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  *
    padding 0
    margin 0
  .banner
    overflow hidden
    height 0
    padding-bottom 55%
    position relative
    background: #f00;
    .banner-img
      width 100%
      background #000
    .banner-info
      position absolute
      left 0
      right 0
      bottom 0
      height 60px
      line-height 60px
      display flex
      color #fff
      background linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8))
      .banner-title
        flex 1
      .banner-num
        width 120px
        height 40px
        text-align center
        line-height 40px
        border-radius 10px
        margin 10px 20px 10px 0
        background #000
        span
          font-size 20px
</style>
