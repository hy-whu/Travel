<template>
  <div>
    <div class="recommend-title">周末去哪ws</div>
    <ul>
      <li v-for="item in weekendList" :key="item.id">
        <div class="item-img-wrapper">
          <img :src=item.imgUrl alt="img">
        </div>
        <div class="info">
          <div class="info-title">{{item.title}}</div>
          <div class="info-desc">{{item.desc}}</div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeWeekend',
  props: {
    weekendList: {
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
  .recommend-title
    height 80px
    background-color: #ddd;
    letter-spacing 16px
    font-size 28px
    line-height 80px
    color $darkTextColor
    text-indent 10px
  .item-img-wrapper
    img
      width 100%
  .info
    .info-title
      font-size 32px
      color: $darkTextColor
      margin 15px 10px
    .info-desc
      font-size 26px
      color #ccc
      margin 0 0 20px 10px
</style>
