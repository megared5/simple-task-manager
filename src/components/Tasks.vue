<template>
  <div class="tasks-wrapper">
    <Task
      :task="task"
      @deleteTask="$emit('deleteTask', task.taskId)"
      v-for="task in tasks"
      :key="task.taskId"
    />
  </div>
</template>

<script>
import Task from "./Task.vue";
export default {
  name: "Tasks",
  props: {
    tasks: Object,
  },
  components: {
    Task,
  },
};
</script>

<style></style>
