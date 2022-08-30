<template>
  <!-- want to bring in the task array as prop, loop through them, then display a task to the page -->
  <div :key="task.id" v-for="task in tasks">
    <Task @delete-task="$emit('delete-task', task.id)" :task="task" />
  </div>
</template>

<script>
import Task from "./Task.vue";

export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
  // declare emits here that we will pass up to app.vue
  emits: ["delete-task"],
};
</script>
