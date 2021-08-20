<template>
  <div class="header-wrapper">
    <div class="header-title">
      <h1>Simple task manager</h1>
      <button class="add-task-button" @click="$emit('showAddTaskForm')">
        +
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style>
/* #region Header title styles */
.header-wrapper {
  padding: 0 0 1em;
  margin: 0 0 1em;
  border-bottom: 1px solid var(--item-background);
}
.header-title {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.header-title > h1 {
  margin: 0;
  color: var(--text-color);
  font-size: 18px;
  font-weight: 300;
}
.add-task-button {
  cursor: pointer;
  border-radius: 3px;
  background-color: var(--item-background);
  color: var(--text-color);
  border: var(--border);
  padding: 0.5em 1em;
}
.add-task-button:hover {
  color: var(--button-hover-color);
  background-color: var(--theme-color);
}
.add-task-button:active {
  background-color: var(--darker-theme-color);
}
/* #endregion */
</style>
