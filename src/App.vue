<template>
  <header>
    <h1>Todo</h1>
    <img src="/images/icon-moon.svg" alt="switch to dark" />
  </header>

  <section class="input">
    <IconCircle class="input-circle" />
    <input
      type="text"
      placeholder="Create a new todo.."
      v-model="newTaskInput"
      @keyup.enter="addTask"
    />
  </section>

  <section class="todos">
    <ul>
      <li v-for="item in taskList" :key="item">
        <IconCircle />
        <IconCheck />
        <input type="checkbox" class="sr-only" />
        <p>{{ item }}</p>
        <IconDelete />
      </li>
      <li>
        <p>{{ taskList.length }} items left</p>
        <p>Clear Completed</p>
      </li>
    </ul>
  </section>

  <section class="filter">
    <ul>
      <li class="active">All</li>
      <li>Active</li>
      <li>Completed</li>
    </ul>

    <p class="instructions">Drag and drop to reorder list</p>
  </section>
</template>

<script>
import { reactive, toRefs } from "vue";
import IconCircle from "./components/IconCircle.vue";
import IconCheck from "./components/IconCheck.vue";
import IconDelete from "./components/IconDelete.vue";

export default {
  name: "App",
  components: {
    IconCircle,
    IconCheck,
    IconDelete,
  },
  setup() {
    const state = reactive({
      newTaskInput: "",
      taskList: [],
    });

    const addTask = () => {
      state.taskList.push(state.newTaskInput);
      state.newTaskInput = '';
    };

    return {
      ...toRefs(state),
      addTask,
    };
  },
};

// Complete online Javascript course
// Jog around the park 3x
// 10 minutes meditation
// Read for 1 hour
// Pick up groceries
// Complete Todo App on Frontend Mentor

</script>
