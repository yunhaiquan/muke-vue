<template>
  <div class="city">
    <city-header></city-header>
    <city-search :city='city'></city-search>
    <city-list :hotCity='hotCity' :city='city' :letter='letter'></city-list>
    <city-alphabet :city='city' @change='letterChange' ></city-alphabet>
  </div>
</template>

<script>
import CityHeader from './components/header'
import CitySearch from './components/search'
import CityList from './components/list'
import CityAlphabet from './components/alphabet'
import axios from 'axios'
export default {
  name: 'City',
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet
  },
  data () {
    return {
      hotCity:[],
      city: null,
      letter: ''
    }
  },
  mounted () {
    this.getCityInfo()
  },
  methods: {
    getCityInfo() {
      axios.get('/static/mock/city.json').then((res) => {
        if (res.data.ret && res.data) {
          const data = res.data.data
          this.hotCity = data.hotCities
          this.city = data.cities
        }
      })
    },
    letterChange (letter) {
      this.letter = letter
    }
  }
}
</script>
