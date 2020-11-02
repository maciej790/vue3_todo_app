<template>
    <div class="temperatures">
        <div class="temp_actual">
            <p>{{temp}}</p>
        </div>
        <div class="temp_min">
            <p>{{temp_min}}</p>
        </div>
        <div class="temp_max">
            <p>{{temp_max}}</p>
        </div>
    </div>
</template>

<script>
export default {
  name: "Temperatures",

  props: {
      temp:{
          type: Number,
          required: false
      },

      temp_min:{
          type: Number,
          required: false
      },

      temp_max:{
          type: Number,
          required: false
      }
  }

};
</script>

<style lang="scss" scoped>
.temperatures{
    width: 100%;
    height: auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: 300px;
    text-align: center;

        .temp_actual{
            width: 100px;
            height: 100px;
            margin-bottom: 50px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .temp_min{
            width: 100px;
            height: 100px;
            margin-bottom: 50px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .temp_max{
            width: 100px;
            height: 100px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
}
</style>
