<template>
  <div>
    <div class="search">
      <input type="text" v-model="keyword" placeholder="please input city name" class="search-input">
    </div>
    <div class="search-content" v-show="keyword" ref="search">
      <ul>
        <li class="search-item" v-for="item of list" :key="item.id">{{item.name}}</li>
        <li class="search-item" v-show="!list.length">未找到</li>
      </ul>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'citySearch',
  props: {
    cities: {
      type: Object
    }
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach(value => {
            if (value.spell.indexOf(this.keyword) > -1 ||
            value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.search)
  }
}
</script>

<style lang="stylus" scoped>
  @import "~style/variables.styl"
  *
    padding 0
    margin 0
    list-style none
  .search
    height 80px
    background $bgColor
    padding 0 10px
    line-height 80px
    margin-top -1px
    .search-input
      box-sizing border-box
      width 100%
      height 64px
      text-align center
      line-height 64px
      border-radius 6px
      border 0
      outline none
      color #666
      padding 0 10px
  .search-content
    z-index 1
    overflow hidden
    position absolute
    top 165px
    left 0
    right 0
    bottom 0
    background-color #eee
    .search-item
      line-height 62px
      padding-left 20px
      color #666
      background #fff
</style>
