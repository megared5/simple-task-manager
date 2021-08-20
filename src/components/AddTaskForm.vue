<template>
  <div class="add-new-task-wrapper">
    <form class="add-new-task-form" @submit.prevent="addNewTask">
      <h1>Add new task</h1>
      <input
        type="text"
        class="add-new-task-input"
        placeholder="Task name"
        v-model="newTask.taskTitle"
      />
      <input
        type="text"
        class="add-new-task-input"
        placeholder="Task date"
        v-model="newTask.taskDate"
      />
      <div class="set-reminder-checkbox-wrapper">
        <input
          type="checkbox"
          class="set-reminder-checkbox"
          name="set-reminder"
          id="set-reminder"
          v-model="newTask.taskReminder"
        />
        <label for="set-reminder">Set reminder</label>
      </div>
      <div class="add-new-task-form-controls">
        <button
          type="reset"
          class="cancel-button"
          @click="$emit('closeAddTaskForm')"
        >
          Cancel</button
        ><input type="submit" class="confirm-new-task" value="Add new task" />
      </div>
      <ErrorMessage v-show="showErrorMessage" />
    </form>
  </div>
</template>

<script>
import ErrorMessage from "./ErrorMessage.vue";
export default {
  name: "AddTaskForm",
  data() {
    return {
      showErrorMessage: false,
      newTask: {
        taskTitle: "",
        taskDate: "",
        taskReminder: false,
        taskId: 0,
      },
    };
  },
  components: {
    ErrorMessage,
  },
  methods: {
    addNewTask() {
      if (!this.newTask.taskTitle) {
        this.showErrorMessage = true;
        setTimeout(() => {
          this.showErrorMessage = false;
        }, 3000);
      } else {
        this.newTask.taskId = Math.random() * 1000;
        !this.newTask.taskDate ? (this.newTask.taskDate = "No date") : null;
        this.$emit("addNewTask", this.newTask);

        this.newTask.taskTitle = "";
        this.newTask.taskDate = "";
        this.newTask.taskReminder = false;
        this.showErrorMessage = false;
      }
    },
  },
};
</script>

<style>
/* #region Add new task styles */
.add-new-task-wrapper {
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  z-index: 2;
  position: fixed;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.2);
}
.add-new-task-form > h1 {
  border: var(--border);
  font-size: 12px;
  font-weight: 300;
  color: var(--text-color);
  width: fit-content;
  margin: 0 0 0.5em;
  padding: 0.5em 1em;
  border-radius: 3px;
  font-weight: 400;
  background-color: var(--lighter-panel-background);
}
.add-new-task-form {
  width: 400px;
  background-color: var(--item-background);
  display: flex;
  flex-direction: column;
  border-radius: 3px;
  padding: 1em;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1);
}

/* #region Input styles */
::placeholder {
  color: var(--darker-text-color);
  font-weight: 500;
  font-size: 12px;
}
.add-new-task-input {
  font-weight: 400;
  background-color: transparent;
  padding: 1em 0.5em;
  margin: 0.5em 0;
  border: none;
  border-bottom: 1px solid var(--darker-text-color);
  color: var(--text-color);
}
.add-new-task-input:hover,
.add-new-task-input:active,
.add-new-task-input:focus {
  border-radius: 3px;
  outline: none;
  background-color: var(--input-hover);
}
.set-reminder-checkbox-wrapper {
  margin: 1em 0 0;
  display: flex;
  align-items: center;
}
.set-reminder-checkbox-wrapper > label {
  font-size: 12px;
  font-weight: 500;
  color: var(--darker-text-color);
}
.add-new-task-form-controls {
  margin-top: 1em;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.confirm-new-task,
.cancel-button {
  border: var(--border);
  flex-basis: 49%;
  cursor: pointer;
  border-radius: 3px;
  background-color: var(--lighter-panel-background);
  color: var(--text-color);
  padding: 0.5em 1em;
}
.confirm-new-task:hover,
.cancel-button:hover {
  color: var(--button-hover-color);
  background-color: var(--theme-color);
}
.confirm-new-task:active,
.cancel-button:active {
  background-color: var(--darker-theme-color);
}
/* #endregion */

/* #endregion */
</style>
