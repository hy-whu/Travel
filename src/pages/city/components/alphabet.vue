<template>
  <ul class="list">
    <li
      class="item"
      v-for="word in words"
      :key="word"
      :ref = "word"
      @click="handleLetterClick"
      @touchstart="handleTouchStart"
      @touchmove="handleTouchMove"
      @touchend="handleTouchEnd"
    >{{word}}</li>
  </ul>
</template>

<script>
export default {
  name: 'cityAlphabet',
  data () {
    return {
      words: ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'],
      touchStatus: false,
      timer: null
    }
  },
  methods: {
    handleLetterClick (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          // const startY = this.$refs['A'][0].offsetTop
          // const touchY = e.touches[0].clientY - 249
        }, 16)
      // 此处offsetTop与clientY似乎与设计稿高度对不上，留待解决
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~style/variables.styl"
  li
    padding 0
    margin 0
    list-style none
  ul
    padding 0
    margin 0
  .list
    display flex
    flex-direction column
    align-items center
    justify-content center
    position absolute
    right 0
    top 164px
    bottom 0
    width 30px
    .item
      display block
      width 30px
      height 38px
      line-height 38px
      color $bgColor
</style>
