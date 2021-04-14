<template>
  <div id="app">
    <div class="flex justify-center items-center relative top-32 gap-3">
      <input
        type="text"
        placeholder="Escreva uma cidade aqui para consultar"
        ref="inputCity"
        class="shadow-sm p-4 rounded-md border-gray-300 focus:outline-none focus:ring-2 focus:ring-indigo-400 focus:border-transparent text-center w-96 text-indigo-400 font-medium text-md focus:"
      >
      <button @click="search" class="bg-indigo-400 text-white p-3 rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-opacity-50 shadow-md">
        <img src="https://www.flaticon.com/svg/vstatic/svg/4272/4272864.svg?token=exp=1618436010~hmac=abf02341a597e76cb1b20de4485b2a5b" width="30">
      </button>
    </div>
    <Weather v-if="visible" :cityProp="city"/>
  </div>
</template>

<script>
import Weather from '@/components/Weather.vue'

export default {
  components: {
    Weather
  },
  data() {
    return {
      visible: false,
      city: ''
    }
  },
  methods: {
    search() {
      if (this.city.value === '') {
        this.visible = false
      } else {
        this.city = this.$refs['inputCity'].value
        this.visible = true
      }
    }
  },
}
</script>

<style lang="postcss">
body, html {
  @apply bg-indigo-100;
}
</style>
