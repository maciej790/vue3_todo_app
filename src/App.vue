<template>
  <div>
      <Board />
  </div>
</template>

<script>

import Board from './components/Board.vue'

export default {
  name: 'App',
  components: {
    Board
  }
}
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body{
    background-image: linear-gradient(to right top, #051937, #004d7a, #008793, #00bf72, #a8eb12);
    background-repeat: no-repeat;
    font-family: 'Open Sans Condensed', sans-serif;
    min-height: 100vh;
  }
</style>
