<template>
  <div>
    <home-header></home-header>
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
import { mapState } from 'vuex'

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
      lastCity: '',
      swiperList: [],
      iconList: [],
      weekendList: [],
      recommendList: []
    }
  },
  computed: {
    ...mapState(['city'])
  },
  methods: {
    getItemInfo() {
      axios.get('/static/mock/index.json?' + this.city).then((res) => {
        if (res.data.ret) {
          const data = res.data.data
          this.swiperList = data.swiperList
          this.iconList = data.iconList
          this.weekendList = data.weekendList
          this.recommendList = data.recommendList
        }
      })
    }
  },
  mounted() {
    this.lastCity = this.city
    this.getItemInfo()
  },
  activated() {
    if (this.lastCity !== this.city) {
      this.lastCity = this.city
      this.getItemInfo()
    }
  }
}
</script>

<style>

</style>