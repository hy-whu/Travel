<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <ul>
      <li v-for="item in recommendList" :key="item.id">
        <div class="item-img-wrapper">
          <img :src=item.imgUrl alt="img">
        </div>
        <div class="info">
          <div class="info-title">{{item.title}}</div>
          <div class="info-desc">{{item.desc}}</div>
          <button class="info-button">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    recommendList: {
      type: Array
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~style/variables.styl"
  ul
    padding 0
    margin: 0
  li
    padding 0
    margin 0
    list-style none
    display flex
    height 188px
  img
    padding 0
    margin: 0
  .recommend-title
    height 80px
    line-height:80px
    background: #eee
    font-size 30px
    text-align center
    color $darkTextColor
    letter-spacing 16px
  .item-img-wrapper
    flex 0 0 20%
    img
      display block
      margin 24px 0 0 24px
      width 150px
      height 150px
  .info
    flex:1
    margin-left 20px
    .info-title
      font-size 32px
      color: $darkTextColor
      margin-top 30px
      font-weight bold
    .info-desc
      font-size 26px
      color #ccc
      margin-top 15px
    .info-button
      margin-top 8px
      background #ff9300
      color #fff
      font-size 26px
      border-radius 3px
      padding 6px
</style>
