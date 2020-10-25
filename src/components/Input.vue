<template>
  <div>
    <div class="input_box">
      <input
        type="text"
        placeholder="Type Your task here"
        @change="$emit('handle-from-child', $event.target.value)"
        v-model="input"
      />
      <button @click="$emit('handle-add-item'), clear()">Add task</button>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  name: "Input",

  setup() {

    const input = ref('')

    const clear = () =>{
      input.value = ''
    }


    return{
      input,
      clear
    }
  }
}
</script>

<style scoped>
.input_box {
  width: 100%;
  height: auto;
  margin-top: 30px;
  display: flex;
  justify-content: space-evenly;
}

input {
  height: 40px;
  width: 40%;
  text-align: center;
  border: 2px solid #487b8b;
  border-radius: 100px;
  background-color: transparent;
  outline: none;
}

button {
  width: 15%;
  text-align: center;
  border-radius: 100px;
  background-color: #487b8b;
  border: none;
  color: white;
  font-weight: bold;
  outline: none;
}

button:hover {
  cursor: pointer;
}
@media (max-width: 550px) {
  .input_box {
    flex-direction: column;
    align-items: center;
    height: auto;
  }

  button {
    height: 35px;
    width: 40%;
    margin-top: 20px;
  }

  input {
    width: 60%;
  }
}
</style>
