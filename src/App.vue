<template>
  <div class="wrapper">
    <div class="box">
      <SearchInput :value='state.InputValue' @emit-from-input='handleChange($event)'/>
    </div>
  </div>
</template>

<script>
import SearchInput from './components/SearchInput.vue'
import { reactive } from 'vue'
import axios from 'axios'
export default {
  name: 'App',
  components: {
    SearchInput,
  },

  setup(){
    const state = reactive({
      InputValue: '',
      resoults: [
        {id: ''},
        {location: ''},
        {temp: ''},
        {temp_min: ''},
        {temp_max: ''},
        {weather_state_img: ''},
        {humidity: ''},
        {speed: ''},
        {pressure: ''}
      ]
    })


    const handleChange = (payload) =>{
        const location = payload

        const url = `http://api.openweathermap.org/data/2.5/weather?q=${location}&appid=962e96c7edd5b917153804d1e003d0ff&units=metric`

        axios.get(url)
        .then(function (response) {

          console.log(response)

          const stateProperty = state.resoults
          const apiResoult = response.data
          const apiResoultMain = response.data.main
          const iconCode = apiResoult.weather[0].icon 
          const iconUrl = `http://openweathermap.org/img/wn/${iconCode}@2x.png`
  
          stateProperty[0].id = apiResoult.id
          stateProperty[1].location = apiResoult.name
          stateProperty[2].temp = apiResoultMain.temp
          stateProperty[3].temp_min = apiResoultMain.temp_min
          stateProperty[4].temp_max = apiResoultMain.temp_max
          stateProperty[5].weather_state_img = iconUrl
          /*
            stateProperty[6].humidity = apiResoultMain.humidity
            stateProperty[7].speed = apiResoult.weather.wind[1]
          */

  
          console.log(state.resoults)

        })
        .catch(err => {
          //errors
          console.log(err);
        })
    }

    return{
      state,
      handleChange
    }
  }

}

</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-size: 18px;
}

body{
  background: rgb(131,58,180);
  background: linear-gradient(180deg, rgba(131,58,180,1) 0%, rgba(101,168,185,1) 0%, rgba(148,110,188,1) 0%, rgba(52,167,200,1) 0%, rgba(118,138,191,1) 61%, rgba(249,139,252,1) 100%);
  width: 100%;
  height: 100vh;
  
    .wrapper{
      width: 100%;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;

        .box{
          width: 75%;
          height: auto;
          display: flex;
          justify-content: center;
          align-items: center;
        }
    }
}

</style>