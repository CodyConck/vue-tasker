<template>
  <div class="container">
    <!-- title "task tracker" is passed as prop to component -->
    <Header title="Task Tracker" />
    <!-- this component will be dynamic and change as we update tasks -->
    <Tasks @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks.vue";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
  },
  // lifecycle method
  data() {
    return {
      tasks: [],
    };
  },
  // emitted up via task.vue and tasks.vue
  methods: {
    deleteTask(id) {
      // adds confirm warning if deleting task
      if (confirm("Are you sure?")) {
        // using filter() passing in task, filter takes a function. we are telling it to filter the task ids and bring back the tasks with an id that dont match the one we just clicked to delete
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doc Appt",
        day: "March 12 at 2:30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "School Mtg",
        day: "March 14 at 1:00pm",
        reminder: true,
      },
      {
        id: 3,
        text: "Grocery Shopping",
        day: "March 15 at 5:30pm",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
