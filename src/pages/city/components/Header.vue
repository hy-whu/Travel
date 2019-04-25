<template>
  <div class="header">
    <router-link to="/">
      <div class="header-left">
        <span class="iconfont arrow-left">&#xe624;</span>
      </div>
    </router-link>
    <div class="header-title">city select</div>
  </div>
</template>

<script>
export default {
  name: 'cityHeader'
}
</script>

<style lang="stylus" scoped>
  @import "~style/variables.styl"
  a
    text-decoration none
  *
    padding 0
    margin 0
  .header
    position relative
    .header-left
      width: 64px
      height $headerHeight
      line-height $headerHeight
      position absolute
      left 0
      .arrow-left
        display: block
        text-align: center
        font-size: 35px
        color #fff
    .header-title
      height $headerHeight
      line-height $headerHeight
      text-align center
      color #fff
      background-color $bgColor
      font-size 32px
</style>
