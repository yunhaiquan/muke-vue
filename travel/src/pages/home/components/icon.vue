<template>
  <swiper :options="swiperOption">
    <swiper-slide class="icon-wrapper" v-for="(page,index) of pages" :key="index">
      <div class="icon" v-for="item of page" :key="item.id">
        <img class="icon-img" :src="item.imgUrl" alt="">
        <p class="icon-text">{{item.desc}}</p>
      </div>
    </swiper-slide>
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
</template>

<script>
export default {
  name:'HomeIcon',
  props: {
    iconList: Array
  },
  data () {
    return {
      swiperOption: {
        loop:true,
        initialSlide :1
     }
   }
 },
 computed: {
   pages () {
     const pages = []
     this.iconList.forEach((item,index) => {
       const page = Math.floor(index/8)
       console.log(index)
       if (!pages[page]){
         pages[page] = []
       }
       pages[page].push(item)
     })
     return pages
   }
 }
}
</script>

<style lang="stylus" scoped>
@import '~styles/mixins.styl'
  .icon-wrapper
    width: 100%
    height: 3.7rem
    display: flex
    flex-wrap: wrap
    overflow: hidden  
    .icon
      width: 25%
      height: 1.5rem;
      padding-top: 0.2rem 
      .icon-img
         display: block
         width: 1.1rem
         height: 1.1rem
         margin: 0 auto
      .icon-text
        margin-top: .1rem
        color: #212121
        font-size: .28rem
        text-align center
        ellipsis()
</style>
