<template>
  <ul class="list">
    <li class="item" v-for="item in letters" :key="item" :ref="item"
        @click='letterClick'
        @touchstart='touchstart'
        @touchmove='touchmove'
        @touchend='touchend'
        >
      {{item}}
    </li>
  </ul>
</template>
<script>
export default {
  name: 'CityAlphabet',
  props:{
    city: Object
  },
  data () {
    return {
      touch:false
    }
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.city) {
        letters.push(i)    
      }
      return letters
    }
  },
  methods: {
    letterClick (e) {
      this.$emit('change', e.target.innerText)
    },
    touchstart () {
      this.touch = true
    },
    touchmove (e) {
      if (this.touch) {
        const startPosition = this.$refs.A[0].offsetTop
        const fingerY = e.touches[0].clientY - 79
        const index = Math.floor((fingerY - startPosition) / 20)
        
        if (0<= index <=25){
          this.$emit('change', this.letters[index])
          console.log(index)
        }
      }
    },
    touchend () {
      this.touch = false
    }
  }

}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .list
    display: flex
    flex-direction: column
    justify-content: center
    position: absolute
    top: 1.58rem
    right: 0
    bottom: 0
    width: .4rem
    .item
      line-height: .4rem
      text-align: center
      color: $bgColor
</style>