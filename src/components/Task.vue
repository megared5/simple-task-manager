<template>
  <div
    :class="[task.taskReminder ? 'task-has-reminder' : '', 'task-wrapper']"
    @dblclick="
      () => {
        task.taskReminder = !task.taskReminder;
      }
    "
  >
    <h1 @click="toggleTaskTitleInput" v-show="!showTaskTitleInput">
      {{ task.taskTitle }}
    </h1>
    <input
      class="task-title-input"
      :id="taskTitleInputId"
      type="text"
      placeholder="Task name"
      v-show="showTaskTitleInput"
      v-model="task.taskTitle"
      @mouseleave="toggleTaskTitleInput"
      @blur="
        () => {
          !task.taskTitle ? (task.taskTitle = 'Empty Task') : null;
          showTaskTitleInput = false;
        }
      "
    />
    <p v-show="!showTaskDateInput" @click="toggleTaskDateInput">
      {{ task.taskDate }}
    </p>
    <input
      class="task-date-input"
      :id="taskDateInputId"
      type="text"
      placeholder="Task date"
      v-show="showTaskDateInput"
      v-model="task.taskDate"
      @mouseleave="toggleTaskDateInput"
      @blur="
        () => {
          !task.taskDate ? (task.taskDate = 'No date') : null;
          showTaskDateInput = false;
        }
      "
    />
    <button
      class="delete-task-button"
      @click="$emit('deleteTask', task.taskId)"
    >
      Delete
    </button>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  data() {
    return {
      showTaskTitleInput: false,
      showTaskDateInput: false,
      taskTitleInputId: 0,
      taskDateInputId: 0,
    };
  },
  methods: {
    toggleTaskTitleInput() {
      this.showTaskTitleInput = true;
      this.showTaskDateInput = false;
      document.getElementById(this.taskTitleInputId).focus();
    },
    toggleTaskDateInput() {
      this.showTaskDateInput = true;
      this.showTaskTitleInput = false;
      document.getElementById(this.taskDateInputId).focus();
    },
  },
  mounted() {
    this.taskTitleInputId = (Math.random() * 1000).toString();
    this.taskDateInputId = (Math.random() * 1000).toString();
  },
};
</script>

<style>
.task-wrapper {
  border-radius: 3px;
  cursor: pointer;
  color: var(--text-color);
  border: 0 solid var(--item-background);
  background-color: var(--item-background);
  margin: 1em 0;
  padding: 1em 2em;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1);
  border: var(--border);
}
.task-wrapper:hover {
  background-color: var(--lighter-item-background);
}
.task-has-reminder {
  border-left: 5px solid var(--theme-color);
}
.task-wrapper > h1 {
  margin: 12px 0;
  width: fit-content;
  font-size: 18px;
  font-weight: 500;
}
.task-wrapper > p {
  margin: 12px 0;
  width: fit-content;
  color: var(--darker-text-color);
  font-size: 12px;
  font-weight: 300;
}
.delete-task-button {
  cursor: pointer;
  border-radius: 3px;
  background-color: var(--lighter-panel-background);
  color: var(--text-color);
  margin-top: -50px;
  float: right;
  padding: 0.5em 1em;
  border: var(--border);
}
.delete-task-button:hover {
  color: var(--button-hover-color);
  background-color: var(--theme-color);
}
.delete-task-button:active {
  background-color: var(--darker-theme-color);
}
.task-title-input,
.task-date-input {
  font-size: 18px;
  font-weight: 500;
  background-color: transparent;
  padding: 0;
  margin: 12px 0 0;
  border: none;
  border-bottom: 1px solid var(--darker-text-color);
  color: var(--text-color);
}
.task-date-input {
  font-size: 12px;
  font-weight: 300;
  margin: 0 0 12px;
}
.task-title-input:hover,
.task-date-input:hover,
.task-title-input:active,
.task-date-input:active,
.task-title-input:focus,
.task-date-input:focus {
  border-radius: 3px;
  outline: none;
  background-color: var(--input-hover);
}
</style>
