<template>
  <div v-if="dataWeather" class="bg-indigo-100 h-screen flex justify-center items-center">
      <Details
        :cloud="dataWeather.current.cloud"
        :humidity="dataWeather.current.humidity"
        :windDir="dataWeather.current.wind_dir"
        :windKph="dataWeather.current.wind_kph"
        :feelslikeC="dataWeather.current.temp_c"
    />
      <div
        class="flex flex-col p-14 rounded-2xl bg-gray-100 shadow-xl main-container justify-beetwen items-center text-center gap-2 font-medium text-gray-500 relative -left-5"
      >
        <h1>{{ dataWeather.location.name }}</h1>
        <span class="text-4xl temp">{{ dataWeather.current.temp_c }}°C</span>
        <figure class="condition flex flex-col">
            <img
                :src="dataWeather.current.condition.icon"
                alt="Imagem demonstrativa do clima atual"
                class="self-center"    
            >
            <figcaption>{{ dataWeather.current.condition.text }}</figcaption>
        </figure>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

import Details from './Details'

export default {
    components: {
        Details,
    },
    data() {
        return {
            key: '4ee720518e2947c3b41142248211404',
            dataWeather: null,
            forecastday: null,
            city: this.cityProp
        }
    },
    name: 'App',
    created() {
        this.newRequestAPI()
    },
    methods: {
        newRequestAPI() {
        axios
            .get(`http://api.weatherapi.com/v1/forecast.json?key=${this.key}&q=${this.city}&aqi=no&lang=pt`)
            .then(response => {
                const data = response.data
                this.dataWeather = data
                
                const forecastday = this.dataWeather.forecast.forecastday[0]
                this.forecastday = forecastday
            })
        }
    },
    props: ['cityProp'],
    watch: {
        cityProp() {
            this.city = this.cityProp
            this.newRequestAPI()
        }
    }
}
</script>

<style scoped>
</style>
