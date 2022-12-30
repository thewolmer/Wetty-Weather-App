<template>
    <div class="justify-center items-center">
    <h1 class="text-center mb-10 text-4xl font-extrabold">Wetty Weather App</h1>
  </div>
  <div class="flex justify-center gap-2">
      <div class="entercity">
          <input
          v-model="data.city"
          class="text-neutral-100 font-medium px-2 py-2 rounded-md text-center focus:ring-4 focus:outline-none focus:ring-[#41b883] bg-neutral-700"
          placeholder="Enter the city"
          @keyup.enter="getWeather"
          type="text">
        </div>
        <button @click="getWeather" class="bg-neutral-700 hover:bg-neutral-500 rounded-md px-2 text-neutral-200  focus:outline-none ">Get Wetty</button>
</div>
    <div class="weather "
  v-if="data.weather">
    <h1 class=" mt-8"> {{ data.weather.location.name }}, {{ data.weather.location.country }}</h1>
    <h2 class="text-5xl text-[#41b883] font-extrabold m">{{ data.weather.current.temp_c }}&deg;</h2>
    <h3 class="font-bold">{{ data.weather.current.condition.text }}</h3>
    <code class="font-bold text-sm"> at {{ data.weather.location.localtime }}</code>
  </div>
  <div class="nodata" v-else>
    <h1 class="text-xl my-7 font-extralight">Enter the city first you dumbfuck.</h1>
  </div>
</template>

<script>
import { reactive } from 'vue'
import  axios  from 'axios'



export default {
    name: 'ShowData',
  setup() {
    let data = reactive({
      city: '',
      weather: null
    })
    
    const apiUrl = 'https://api.weatherapi.com/v1/current.json'
    const apiKey = 'cfe16a00d2f54a57bb6134126223012'

   

    const getWeather = () => {
      axios(`${ apiUrl }?key=${ apiKey }&q=${ data.city }`) .then(response => {
        data.weather = response.data
      })
     
    }
    return {
      data,
      getWeather
    }
  }

}
</script>

