<template>
  <div class="container" @click="handleGallaryClick">
    <div class="wrapper">
      <swiper :options="swiperOption">
        <swiper-slide v-for="item of gallaryImgs" :key="item.id">
          <img class="swiper-img" :src="item" alt="img">
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonGallary',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observeParents: true,
        observer: true
      }
    }
  },
  props: {
    gallaryImgs: {
      type: Array
    }
  },
  methods: {
    handleGallaryClick () {
      this.$emit('close')
    },
    handleMaskBug () {
      console.log(this.$store.state.showReturn)
      if (!this.$store.state.showReturn) {
        this.$store.state.showReturn = true
      }
    }
  },
  mounted () {
    this.handleMaskBug()
  }
}
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-container
    overflow inherit
  .container
    display flex
    position absolute
    top 0
    left 0
    right 0
    bottom 0
    z-index 10
    flex-direction column
    justify-content center
    background #000
    .wrapper
      width 100%
      height 0
      padding-bottom 100%
      .swiper-pagination
        color #fff
        bottom -10px
      .swiper-img
        width 100%
</style>
