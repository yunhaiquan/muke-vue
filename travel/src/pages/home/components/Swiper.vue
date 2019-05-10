<template>
  <div class="wrapper">
    <swiper :options="swiperOption">
      <!-- slides -->
      <swiper-slide v-for="item of list" :key="item.id">
        <img class="swiper-img" :src="item.src" alt="">
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name:'HomeSwiper',

  data () {
    return {
      swiperOption:{
        pagination: '.swiper-pagination',     
        loop: true
      },
      list:[
        {id:1,src:'https://pic.tujia.com/upload/resourcespic/day_190417/201904171518582360.jpg'},
        {id:2,src:'https://pic.tujia.com/upload/resourcespic/day_190417/201904171518582360.jpg'},
        {id:3,src:'https://pic.tujia.com/upload/resourcespic/day_190314/201903141930453018.png'},
        {id:4,src:'https://pic.tujia.com/upload/resourcespic/day_190411/201904111109509637.jpg'}
      ]
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
    padding-bottom: 77.3%
    background: #eee
    .swiper-img
      width: 100% 
</style>
