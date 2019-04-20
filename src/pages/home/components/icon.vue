<template>
  <div class="icons">
    <div class="icon" v-for="item in items" :key="item.id">
      <img :src=item.imgUrl alt="img">
      <div class="text">{{item.desc}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeIcon',
  props: {
    items: {
      type: Array
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~style/variables.styl"
  @import "~style/mixin.styl"
  .icons
    overflow hidden
    height 0px
    padding-bottom 50%
    display flex
    flex-wrap: wrap
    .icon
      /*width 25%*/
      height 0
      padding-bottom 25%
      position relative
      flex 0 0 25%
      img
        display block
        width 80px
        height 80px
        margin 0 auto
        margin-top 40px
      .text
        width 160px
        margin 10px auto
        font-size 20px
        text-align center
        color: $darkTextColor
        ellipse()
</style>
