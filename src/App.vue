<script>
import Weather from './components/Weather.vue'
import axios from "axios";
export default {
  name: 'App',
  components:{
    Weather
  },
  data(){
    return{
      city: '',
      weatherExist: false,
      data: {}

    }
  },
  methods:{
    async searchWeather(){
      this.weatherExist = false
      await this.$nextTick();;
      const res = await axios.get(`https://api.weatherapi.com/v1/current.json?key=${import.meta.env.VITE_APP_WEATHER_API}&q=${this.city}&aqi=yes`)
      this.data  = res.data
      console.log(this.data)
      this.weatherExist = true


  }
  }
}
</script>

<template>
  <div class="app">
    <div class="header container h-100 p-5">
      <h1 class="mb-5">Weather App</h1>
      <div class="d-flex justify-content-center h-100">
        <div class="searchbar w-50 mx-2">
          <input v-model="city" type="text" class="input form-control" placeholder="Enter a city">
        </div>
        <button @click="searchWeather" class="btn-search  btn btn-primary">Search <i class="fa fa-search"></i></button>
      </div>
    </div>
    <br>
    <div v-if="weatherExist">
      <Weather :data="data" />
    </div>
    <div v-else class="container mx-auto d-block w-25 bg-warning p-3 rounded ">
      <h5>No city Found yet please search </h5>
    </div>
  </div>
</template>

<style scoped>
body{
  background-color: #121212 !important;
}
.header{
  background-color: #212730;
  border-radius: 20px;
  color: #fff;
  text-align: center;
  font-family: 'Franklin Gothic Medium', sans-serif;
  margin-top: 5rem;
}
</style>
