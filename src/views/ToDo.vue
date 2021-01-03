<template>
  <div class="ToDo">
    <h2>To Do List</h2>
    <form action="#">
      <label for="item">Item</label>
      <input type="text" name="item" id="item" />
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
import { defineComponent, reactive } from "vue";

export default defineComponent({
  setup() {
    const todos = reactive([
      {
        text: "First To Do Item",
      },
    ]);

    return {
      todos,
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
