<template>
  <div class="location">
    <p>
      {{ location + ':'}}
    </p>
  </div>
</template>

<script>
export default {
  name: "Location",

  props: {
    location: {
      type: String,
      required: false,
    },
  },
};
</script>

<style lang="scss" scoped>
.location {
    position: absolute;
    top: 100px;
    font-size: 20px;
    letter-spacing: 2px;
    font-weight: bold;
}
</style>
