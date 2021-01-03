<template>
  <div class="ToDo">
    <h2>To Do List</h2>
    <form action="#" @submit.prevent="addToDo">
      <label for="item">Item</label>
      <input type="text" name="item" id="item" v-model="toDoInput" />
      <input type="submit" value="Add" />
    </form>
    <ul class="todolist">
      <li v-for="(item, index) in todos" :key="index">
        {{ item.text }}
      </li>
    </ul>
  </div>
</template>

<script>
import { defineComponent, reactive, ref } from "vue";

export default defineComponent({
  setup() {
    const todos = reactive([]);
    const toDoInput = ref(""); // Ref stores things as objects. {value = ""}
    const addToDo = () => {
      todos.unshift({
        text: toDoInput.value,
      });
      toDoInput.value = "";
    };

    return {
      todos,
      toDoInput,
      addToDo,
    };
  },
});
</script>

<style scoped>
.ToDo {
  border: solid;
  text-align: center;
}
</style>
