<template>
  <div class="ToDo">
    <h2>To Do List</h2>
    <form action="#" @submit.prevent="addToDo">
      <label for="item">Item</label>
      <input type="text" name="item" id="item" v-model="toDoInput" />
      <input type="submit" value="Add" />
    </form>
    <ul class="todolist">
      <li
        v-for="(item, index) in todos"
        :key="index"
        :class="[done ? '' : finished]"
      >
        <span>
          {{ item.text }}
        </span>
        <button v-if="!item.done" @click="markasDone(index)">Finish</button>
        <button @click="deleteItem(index)">Delete</button>
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
        done: false,
      });
      toDoInput.value = "";
    };
    const markasDone = (index) => {
      todos[index].done = true;
    };

    const deleteItem = (index) => {
      if (!confirm("Are you sure?")) {
        return;
      } else {
        todos.splice(index, 1);
        alert("removed");
      }
    };

    return {
      todos,
      toDoInput,
      addToDo,
      markasDone,
      deleteItem,
    };
  },
});
</script>

<style scoped>
.ToDo {
  border: solid;
  text-align: center;
}

.finished {
  background: chartreuse;
}
</style>
