<template>
  <div>
    <home-header></home-header>
    <home-swiper></home-swiper>
    <home-icon></home-icon>  
  </div>
   
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcon from './components/icon'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcon
  },
  data() {
    return {
      city: String
    }
  },
  mounted() {
    this.getItemInfo()
  },
  methods: {
    getItemInfo() {
      axios.get('/static/mock/index.json').then((res) => {
        if (res.data.ret) {
          const data = res.data
          this.city = data.city
          console.log(this.city)
        }
      })
    }
  }
}
</script>

<style>

</style>