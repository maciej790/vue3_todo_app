<template>
  <div class="img">
    <img :src="image" />
  </div>
</template>

<script>
export default {
  name: "Image",

  props: {
    image: {
      type: String,
      required: false,
    },
  },
};
</script>

<style lang="scss" scoped>
    .img{
        position: absolute;
        top: 120px;
        display: flex;
        justify-content: center;
        align-items: center;
        
            img{
                width: 200px;
                height: 200px;
            }
    }
</style>
