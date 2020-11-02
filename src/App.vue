<template>
  <div class="wrapper">
    <div class="box">
      <SearchInput
        :value='state.InputValue'
        :top='state.state'
        @emit-from-input='handleChange($event)'
      />
      <Location 
        v-if='state.state'
        :location='state.results[1].location'
      />
      <Image 
        v-if='state.state'
        :image='state.results[5].weather_state_img'
      />
      <Temperatures 
        v-if='state.state'
        :temp='state.temp'
        :temp_min='state.temp_min'
        :temp_max='state.temp_max'
      />
    </div>
  </div>
</template>

<script>
import SearchInput from "./components/SearchInput.vue";
import Location from "./components/Location.vue";
import Image from "./components/Image.vue";
import Temperatures from './components/Temperatures.vue'

import { computed , reactive } from "vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    SearchInput,
    Location,
    Image,
    Temperatures
  },

  setup() {
    const state = reactive({
      InputValue: "",
      results: [
        { id: "" },
        { location: "" },
        { temp: "" },
        { temp_min: "" },
        { temp_max: "" },
        { weather_state_img: "" },
        { humidity: "" },
        { speed: "" },
        { pressure: "" },
      ],

      temp: computed(
        () => Math.round(state.results[2].temp)
      ),
      temp_min: computed(
        () => Math.round(state.results[3].temp_min)
      ),
      temp_max: computed(
        () => Math.round(state.results[4].temp_max)
      ),
      humidity: computed(
        () => Math.round(state.results[6].humidity)
      ),
      speed: computed(
        () => Math.round(state.results[7].speed)
      ),
      pressure: computed(
        () => Math.round(state.results[8].pressure)
      ),

      state: false,
    });

    const handleChange = (payload) => {
      const location = payload;

      const url = `http://api.openweathermap.org/data/2.5/weather?q=${location}&appid=962e96c7edd5b917153804d1e003d0ff&units=metric`;

      axios
        .get(url)
        .then(function(response) {
          //destructuring JSON from api
          const stateProperty = state.results;
          const apiResoult = response.data;
          const apiResoultMain = response.data.main;
          const iconCode = apiResoult.weather[0].icon;
          const iconUrl = `http://openweathermap.org/img/wn/${iconCode}@2x.png`;

          //add to objects values from api
          stateProperty[0].id = apiResoult.id;
          stateProperty[1].location = apiResoult.name;
          stateProperty[2].temp = apiResoultMain.temp;
          stateProperty[3].temp_min = apiResoultMain.temp_min;
          stateProperty[4].temp_max = apiResoultMain.temp_max;
          stateProperty[5].weather_state_img = iconUrl;
          stateProperty[6].humidity = apiResoultMain.humidity;
          stateProperty[7].speed = apiResoult.wind.speed;
          stateProperty[8].pressure = apiResoultMain.pressure;
               
              

          //change state to display component
          state.state = true;

        })
        .catch((err) => {
          //errors
          console.log(err);
        });
    };

    return {
      state,
      handleChange,
    };
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-size: 18px;
}

body {
  background: rgb(131, 58, 180);
  background: linear-gradient(
    180deg,
    rgba(131, 58, 180, 1) 0%,
    rgba(101, 168, 185, 1) 0%,
    rgba(148, 110, 188, 1) 0%,
    rgba(52, 167, 200, 1) 0%,
    rgba(118, 138, 191, 1) 61%,
    rgba(249, 139, 252, 1) 100%
  );
  width: 100%;
  height: 100vh;
  color: white;
  font-family: 'Roboto', sans-serif;

  .wrapper {
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;

    .box {
      width: 75%;
      height: auto;
      display: flex;
      justify-content: center;
      align-items: center;
    }
  }
}

/*
  .fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

*/
</style>
