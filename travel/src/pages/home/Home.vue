<template>
  <div>
    <home-header :city='city'></home-header>
    <home-swiper :swiperList='swiperList'></home-swiper>
    <home-icon :iconList='iconList'></home-icon>
    <home-recommend :list='recommendList'></home-recommend>  
    <home-weekend :weekendList='weekendList'></home-weekend>
  </div>
   
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcon from './components/icon'
import HomeWeekend from './components//weekend'
import HomeRecommend from './components//recommend'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcon,
    HomeWeekend,
    HomeRecommend
  },
  data() {
    return {
      city: '',
      swiperList: [],
      iconList: [],
      weekendList: [],
      recommendList: []
    }
  },
  mounted() {
    this.getItemInfo()
  },
  methods: {
    getItemInfo() {
      axios.get('/static/mock/index.json').then((res) => {
        if (res.data.ret) {
          const data = res.data.data
          this.city = data.city
          this.swiperList = data.swiperList
          this.iconList = data.iconList
          this.weekendList = data.weekendList
          this.recommendList = data.recommendList
        }
      })
    }
  }
}
</script>

<style>

</style>