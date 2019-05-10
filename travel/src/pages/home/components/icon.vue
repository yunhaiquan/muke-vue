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
  data () {
    return {
      iconList: [
        {
          id: 1,
          desc: '景点描述',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png'
        },
        {
          id: 2,
          desc: '一日游',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png'
        },
        {
          id: 3,
          desc: '杭州必游',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png'
        },
                {
          id: 4,
          desc: '踏青赏花',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/bd/9f7b9b2b60c1502.png'
        },
        {
          id: 5,
          desc: '印象西湖',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/17/99402a22ce4af302.png'
        },
        {
          id: 6,
          desc: '千岛湖',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/75/eca3ce656c886502.png'
        },
                {
          id: 7,
          desc: '杭州野生',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/47/c2b659e048b11602.png'
        },
        {
          id: 8,
          desc: '西溪湿地',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/b8/c5dcdb58deec2402.png'
        },
        {
          id: 9,
          desc: '杭州宋城',
          imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/e3/67df61427c8e1302.png'
        }
      ],
      swiperOption: {
        loop:true,

        
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
