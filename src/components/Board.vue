<template>
  <div class="board">
    <Header />
    <Input
      @handle-from-child="handleFromChild($event)"
      @handle-add-item="addItem"
    />
    <TodoItem :tasks="state.tasks" @remove-element="handleRemoveElement" />
  </div>
</template>

<script>
import Header from "./Header.vue";
import Input from "./Input.vue";
import TodoItem from "./TodoItem.vue";

import { reactive, onMounted } from "vue";
export default {
  name: "Board",
  components: {
    Header,
    Input,
    TodoItem,
  },

  setup() {
    const state = reactive({
      inputValue: "",
      tasks: [],
    });

    //get a task from localstorage
    onMounted(() => {
      state.tasks = JSON.parse(localStorage.getItem("el"));
    });

    const handleFromChild = (payload) => {
      state.inputValue = payload;
    };

    const addItem = () => {
      if (state.inputValue !== "") {
        state.tasks.push({
          id: Math.random() + 1,
          title: state.inputValue,
          complete: false,
        });

        //save task to localstorage
        localStorage.setItem("el", JSON.stringify(state.tasks));

        state.inputValue = "";
      } else {
        alert("First You must type a task!");
      }
    };

    const handleRemoveElement = (payload) => {
      const id = payload;

      const index = state.tasks.findIndex((el) => el.id === id);
      state.tasks.splice(index, 1);

      //remove task from localstorage
      localStorage.setItem("el", JSON.stringify(state.tasks));
    };

    return {
      state,
      handleFromChild,
      addItem,
      handleRemoveElement,
    };
  },
};
</script>

<style>
.board {
  width: 50%;
  height: auto;
  background-color: rgba(255, 255, 255, 0.8);
  margin-left: auto;
  margin-right: auto;
  margin-top: 100px;
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  padding-bottom: 50px;
}
</style>
