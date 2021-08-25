<template>
  <header>
      <h1>Todo</h1>
      <img src="/images/icon-moon.svg" alt="switch to dark" />
    </header>

    <section class="input">
      <IconCircle class="input-circle" />
      <input type="text" placeholder="Create a new todo.." />
    </section>

    <section class="todos">
      <ul>
        <li class="complete">
          <IconCircle />
          <input type="checkbox" class="sr-only" />
          <p>Complete online Javascript course</p>
          <IconDelete />
        </li>
        <li>
          <IconCircle />
          <input type="checkbox" class="sr-only" />
          <p>Jog around the park 3x</p>
          <IconDelete />
        </li>
        <li>
          <IconCircle />
          <input type="checkbox" class="sr-only" />
          <p>10 minutes meditation</p>
          <IconDelete />
        </li>
        <li>
          <IconCircle />
          <input type="checkbox" class="sr-only" />
          <p>Read for 1 hour</p>
          <IconDelete />
        </li>
        <li>
          <IconCircle />
          <input type="checkbox" class="sr-only" />
          <p>Pick up groceries</p>
          <IconDelete />
        </li>
        <li>
          <IconCircle />
          <input type="checkbox" class="sr-only" />
          <p>Complete Todo App on Frontend Mentor</p>
          <IconDelete />
        </li>
        <li>
          <p>5 items left</p>
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
import IconCircle from './components/IconCircle.vue';
import IconCheck from './components/IconCheck.vue';
import IconDelete from './components/IconDelete.vue';

export default {
  name: 'App',
  components: {
    IconCircle,
    IconCheck,
    IconDelete,
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
