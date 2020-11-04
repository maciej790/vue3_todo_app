<template>
    <div class="temperatures">
        <div class="temp_actual">
            <p>{{temp + '°C'}}</p>
        </div>
        <div class="temp_min">
            <u>min:</u>
            <p>{{temp_min + '°C'}}</p>
        </div>
        <div class="temp_max">
            <u>max:</u>
            <p>{{temp_max + '°C'}}</p>
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
    margin-top: 200px;
    text-align: center;

        u{
            margin-bottom: 5px;
        }

        .temp_actual{
            width: 100px;
            height: 50px;
            margin-bottom: 50px;
            display: flex;
            justify-content: center;
            align-items: center;

                p{
                    font-weight: bold;
                    font-size: 55px;
                }
        }

        .temp_min{
            width: 100px;
            height: 50px;
            margin-bottom: 50px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;

                p{
                    font-size: 20px;
                    font-weight: bold;
                }

        }

        .temp_max{
            width: 100px;
            height: 50px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;

                   p{
                    font-size: 20px;
                    font-weight: bold;
                }
        }
}
</style>
