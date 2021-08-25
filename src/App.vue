<template>
  <header>
    <h1>Todo</h1>
    <img src="/images/icon-moon.svg" alt="switch to dark" />
  </header>

  <section class="input">
    <IconCircle class="input-circle"/>
    <input
      type="text"
      placeholder="Create a new todo.."
      v-model="newTaskInput"
      @keyup.enter="addTask"
    />
  </section>

  <section class="todos">
    <ul>
      <li v-for="item in taskInView" :key="item">
        <IconCircle v-show="!item.complete" />
        <IconCheck v-show="item.complete"/>
        <input type="checkbox" v-model="item.complete" :checked="item.complete"/>
        <p>{{ item.label }}</p>
        <IconDelete />
      </li>
      <li>
        <p v-show="currentView === 'All'">{{ allTasksLength }} items left</p>
        <p v-show="currentView === 'Active'">{{ activeTasksLength }} items left</p>
        <p v-show="currentView === 'Completed'">{{ completedTasksLength }} items left</p>
        <p>Clear Completed</p>
      </li>
    </ul>
  </section>

  <section class="filter">
    <ul>
      <li :class="{ active: currentView === 'All' }" @click="setView('All')">All</li>
      <li :class="{ active: currentView === 'Active' }" @click="setView('Active')">Active</li>
      <li :class="{ active: currentView === 'Completed' }" @click="setView('Completed')">Completed</li>
    </ul>

    <p class="instructions">Drag and drop to reorder list</p>
  </section>
</template>

<script>
import { computed, reactive, toRefs } from "vue";
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
      currentView: 'All',
      newTaskInput: "",
      taskList: [{
        label: "Milk",
        complete: false
      }],
    });

    const taskViews = reactive({
      allTasksLength: computed(() => {
        return state.taskList.length
      }),
      activeTasksLength: computed(() => {
        return state.taskList.filter(item => item.complete === false).length
      }),
      completedTasksLength: computed(() => {
        return state.taskList.filter(item => item.complete === true).length
      }),
    })

    const taskInView = computed(() => {
      if(state.currentView === 'All') {
        return state.taskList;
      } else if (state.currentView === 'Active') {
        return state.taskList.filter(item => item.complete === false);
      } else if (state.currentView === 'Completed') {
        return state.taskList.filter(item => item.complete === true);
      } else {
        return state.taskList;
      }
    })

    const setView = viewLabel => {
      state.currentView = viewLabel;
    }

    const addTask = () => {
      state.taskList.push({
        complete: false,
        label: state.newTaskInput,
      });
      state.newTaskInput = '';
    };

    return {
      ...toRefs(state),
      ...toRefs(taskViews),
      addTask,
      taskInView,
      taskViews,
      setView,
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
