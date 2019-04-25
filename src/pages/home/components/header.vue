<template>
  <div class="header">
    <div class="header-left">
      <span class="iconfont arrow-left">&#xe624;</span>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;输入城市/景点/游玩主题</span>
    </div>
    <router-link to="/city">
      <div class="header-right">
        <span>{{this.$store.state.city}}</span>
        <span class="iconfont arrow-down">&#xe634;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'HomeHeader'
}
</script>

<style lang="stylus" scoped>
  @import "~style/variables.styl"
  a
    text-decoration: none
  .header
    height: 86px
    line-height: 86px
    display: flex
    color: #fff
    background: $bgColor
    font-size: 16px /*px*/
    .header-left
      width: 64px
      .arrow-left
        display: block
        text-align: center
        font-size: 35px
    .header-input
      flex: 1
      background : #fff
      border-radius :5px
      margin :12px 20px
      color: #cccccc
      line-height: 62px
      padding-left :20px
    .header-right
      width : 124px
      text-align : center
      font-size : 28px
      span
        display: inline-block
        vertical-align :top
        color #fff
      .arrow-down
        font-size : 40px
</style>
