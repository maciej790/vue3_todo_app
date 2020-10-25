<template>
  <div class="board">
    <Header :date="state.date" />
    <Input
      @handle-from-child="handleFromChild($event)"
      @handle-add-item="addItem"
      :value="inputValue"
    />
    <TodoItem
      :tasks="state.tasks"
      @remove-element="handleRemoveElement"
      @check="check"
    />
  </div>
</template>

<script>
import Header from "./Header.vue";
import Input from "./Input.vue";
import TodoItem from "./TodoItem.vue";

import { reactive, onMounted, computed } from "vue";
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
      today: new Date(),
      date: computed(
        () =>
          state.today.getDate() +
          "/" +
          (state.today.getMonth() + 1) +
          "/" +
          state.today.getFullYear()
      ),
    });

    //get a task from localstorage
    onMounted(() => {
      if (JSON.parse(localStorage.getItem("el")))
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

    //check task
    const check = (payload) => {
      const id = payload;
      const index = state.tasks.findIndex((el) => el.id === id);

      const status = state.tasks[index].complete;

      state.tasks[index].complete = !status;

      localStorage.setItem("el", JSON.stringify(state.tasks));
    };

    return {
      state,
      handleFromChild,
      addItem,
      handleRemoveElement,
      check,
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

@media (max-width: 900px) {
  .board {
    width: 90%;
    margin-top: 50px;
  }
}
</style>
