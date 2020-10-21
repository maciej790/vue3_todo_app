<template>
  <div>
    <div class="item_box">
      <div class="item" v-for="item in tasks" :key="item.id">
        <div
          class="item__title"
          :class="item.complete ? 'completed' : ''"
          @click="$emit('check', item.id)"
        >
          {{ item.title }}
        </div>
        <div class="item__btn">
          <i
            class="fas fa-trash fa-2x"
            @click="$emit('remove-element', item.id)"
          ></i>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "TodoItem",

  props: {
    tasks: String,
  },

  setup() {
    const status = ref("");

    return {
      status,
    };
  },
};
</script>

<style scoped>
.item_box {
  width: 100%;
  height: auto;
  margin-top: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.item {
  width: 80%;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 30px;
}

.item__title {
  width: 80%;
  height: 50px;
  border-radius: 20px;
  background-color: #46c287;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 20px;
}

.item__btn {
  width: 50px;
  height: 50px;
  border-radius: 20px;
  background-color: #46c287;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
}

.item__btn:hover {
  cursor: pointer;
}

.completed {
  color: #487b8b;
  text-decoration: line-through;
}

@media (max-width: 550px) {
  .item_box {
    margin-top: 0;
    width: 100%;
  }

  .item {
    flex-direction: column;
    height: auto;
    width: 100%;
  }

  .item__title {
    height: 35px;
    width: 90%;
    font-size: 18px;
  }

  .item__btn {
    margin-top: 10px;
    font-size: 10px;
    width: 40px;
    height: 40px;
    border-radius: 15px;
  }
}
</style>
