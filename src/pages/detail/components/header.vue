<template>
  <div>
    <router-link tag="div" to="/" class="header-re" v-show="this.$store.state.showReturn">
      <span class="iconfont header-re-button">&#xe624;</span>
    </router-link>
    <div class="header-fixed" v-show="!this.$store.state.showReturn" v-bind:style="opacityStyle"></div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 150) {
        let opacity = top / 270
        opacity = opacity < 1 ? opacity : 1
        this.opacityStyle = {
          opacity
        }
        this.$store.state.showReturn = false
      } else {
        this.$store.state.showReturn = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  .header-re
    position absolute
    top 20px
    left 20px
    width 80px
    height 80px
    border-radius 40px
    background rgba(0,0,0,.8)
    line-height 80px
    text-align center
    .header-re-button
      color #fff
      font-size 30px
  .header-fixed
    position fixed
    top 0
    left 0
    right 0
    height 86px
    background-color rgba(255,255,255,.8)
    z-index 10
</style>
