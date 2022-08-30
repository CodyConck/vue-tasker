<template>
  <!--  can put ternairy within a v bind class to give reminder styling conditionally. this conditionally switches between css classes reminder and task -->
  <div :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>
      {{ task.text }}
      <!-- adding delete icon in tasks h3 -->
      <i @click="onDelete(task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {
    onDelete(id) {
      // need to emit to tasks.vue then app.vue level. wil use custom event named 'delete-task'. pass id as param
      this.$emit("delete-task", id);
    },
  },
};
</script>

<style>
.fas {
  color: red;
}

.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
