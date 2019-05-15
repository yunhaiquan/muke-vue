<template>
  <div class="wrapper">
    <swiper :options="swiperOption">
      <!-- slides -->
      <swiper-slide v-for="item of this.swiperList" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl" alt="">
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name:'HomeSwiper',
  props: {
    swiperList: Array
  },
  data () {
    return {
      swiperOption:{
        pagination: '.swiper-pagination',
        loop: true,
        initialSlide :1
      },
    }
  }
}
</script>
<style lang="stylus" scoped>
   .wrapper >>> .swiper-pagination-bullet-active
     background: #fff
   .wrapper
    overflow: hidden
    width: 100%
    height: 0
    padding-bottom: 31.3%
    background: #eee
    .swiper-img
      width: 100% 
</style>
