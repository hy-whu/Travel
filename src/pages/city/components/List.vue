<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title">
          now-City
        </div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.$store.state.city}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title">hot-City</div>
        <div class="button-list">
          <div class="button-wrapper" v-for="city in hotCities" :key="city.id" @click="handleCityClick(city.name)">
            <div class="button">{{city.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item,key) of cities" :key="key" :ref="key">
        <div class="title">
          {{key}}
        </div>
        <div class="item-list" v-for="i of item" :key="i.id" @click="handleCityClick(i.name)">
          <div class="item">
            {{i.name}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'cityList',
  props: {
    cities: {
      type: Object
    },
    hotCities: {
      type: Array
    },
    letter: {
      type: String
    }
  },
  methods: {
    handleCityClick (name) {
      this.$store.dispatch('changeCity', name)
      this.$router.push('/')
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper)
    // console.log(this.letter)
  },
  watch: {
    letter () {
      // console.log(this.letter)
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        // console.log(this.$refs)
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .list
    overflow hidden
    position absolute
    top 166px
    left 0
    right 0
    bottom 0
    .title
      height 54px
      line-height 54px
      background #eee
      padding-left 20px
      color #666
      font-size 26px
      border-top 1px #ccc solid    /*no*/
      border-bottom 1px #ccc solid /*no*/
    .button-list
      padding 10px 60px 10px 10px
      display flex
      flex-wrap wrap
      .button-wrapper
        flex 0 0 33%
        .button
          margin 10px
          text-align center
          border 2px #ccc solid
          padding 10px 0
          border-radius 6px
    .item-list
      .item
        height 76px
        line-height 76px
        padding-left 20px
        border-bottom 1px solid #ccc
        font-size 28px
</style>
