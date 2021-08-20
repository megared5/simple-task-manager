<template>
  <div class="body-wrapper">
    <Notification
      :showNotification="showNotification"
      :notificationMessage="notificationMessage"
    />
    <AddTaskForm
      @addNewTask="addNewTask"
      @closeAddTaskForm="
        () => {
          showAddTaskForm = !showAddTaskForm;
        }
      "
      v-show="showAddTaskForm"
    />
    <!-- <EditTaskForm
      :targetTask="targetTask"
      @editTask="editTask"
      @closeEditTaskForm="
        () => {
          showEditTaskForm = !showEditTaskForm;
        }
      "
      v-show="showEditTaskForm"
    /> -->
    <div class="body-content">
      <div class="theme-switcher">
        <select @change="changeTheme">
          <option value="0">Dark</option>
          <option value="1">Light</option>
          <option value="2">Light Mega Red</option>
          <option value="3">Dark Mega Red</option>
        </select>
      </div>
      <Header
        @addNewTask="addNewTask"
        @showAddTaskForm="
          () => {
            showAddTaskForm = !showAddTaskForm;
          }
        "
      />
      <Tasks
        :tasks="tasks"
        @deleteTask="deleteTask"
        @passEditTargetTask="showEditTask"
      />
      <p v-show="tasks.length == 0">Task list is empty</p>
    </div>
  </div>
</template>

<script>
import AddTaskForm from "./AddTaskForm.vue";
// import EditTaskForm from "./EditTaskForm.vue";
import Header from "./Header.vue";
import Notification from "./Notification.vue";
import ErrorMessage from "./ErrorMessage.vue";
import Tasks from "./Tasks.vue";
export default {
  name: "Body",
  data() {
    return {
      showAddTaskForm: false,
      // showEditTaskForm: false,
      tasks: [
        {
          taskTitle: "Go to dentist",
          taskDate: "July 28, 7:00 AM",
          taskReminder: false,
          taskId: 0,
        },
        {
          taskTitle: "Go for a walk",
          taskDate: "May 23, 9:00 AM",
          taskReminder: true,
          taskId: 1,
        },
        {
          taskTitle: "Go to theater",
          taskDate: "June 14, 5:00 PM",
          taskReminder: false,
          taskId: 2,
        },
      ],
      // targetTask: {
      //   taskTitle: "",
      //   taskDate: "",
      //   taskReminder: false,
      //   taskId: 0,
      // },
      showNotification: false,
      notificationMessage: { notificationTitle: "", notificationMessage: "" },
    };
  },
  components: {
    Tasks,
    Header,
    ErrorMessage,
    Notification,
    AddTaskForm,
    // EditTaskForm,
  },
  methods: {
    changeTheme(e) {
      switch (e.target.value) {
        case "0":
          document.querySelector("body").className = "";
          break;
        case "1":
          document.querySelector("body").className = "light-theme";
          break;
        case "2":
          document.querySelector("body").className = "megared-theme";
          break;
        case "3":
          document.querySelector("body").className = "dark-megared-theme";
          break;
      }
    },
    deleteTask(Id) {
      this.tasks = this.tasks.filter((taskElement) => {
        return taskElement.taskId != Id;
      });
    },
    addNewTask(newTask) {
      this.showAddTaskForm = !this.showAddTaskForm;
      this.tasks.unshift({
        taskTitle: newTask.taskTitle,
        taskDate: newTask.taskDate,
        taskReminder: newTask.taskReminder,
        taskId: newTask.taskId,
      });
      this.showNotificationMessage(
        `Task added successfully`,
        `Task "${this.tasks[0].taskTitle}" has been added to the list`
      );
    },
    // editTask(targetTask) {
    //   this.tasks.forEach((element) => {
    //     if (element.taskId == targetTask.taskId) {
    //       console.log(element);
    //       this.tasks[this.tasks.indexOf(element)].taskTitle =
    //         targetTask.taskTitle;
    //       this.tasks[this.tasks.indexOf(element)].taskDate =
    //         targetTask.taskDate;
    //       this.tasks[this.tasks.indexOf(element)].taskReminder =
    //         targetTask.taskReminder;
    //       this.showEditTaskForm = false;
    //     }
    //   });
    // },
    // showEditTask(targetTask) {
    //   console.log(this.tasks);
    //   this.targetTask = targetTask;
    //   this.showEditTaskForm = true;
    // },
    showNotificationMessage(notificationTitle, notificationMessage) {
      this.showNotification = true;
      setTimeout(() => {
        this.showNotification = false;
      }, 5000);
      this.notificationMessage.notificationTitle = notificationTitle;
      this.notificationMessage.notificationMessage = notificationMessage;
    },
  },
};
</script>

<style>
.theme-switcher {
  margin: 0 0 1em;
  text-align: center;
}
.theme-switcher > select {
  background-color: var(--item-background);
  color: var(--text-color);
  border-radius: 3px;
  padding: 0.5em 1em;
  border: none;
  outline: none;
}
.theme-switcher > select:hover {
  background-color: var(--lighter-item-background);
}
.body-content {
  border: var(--border);
  backdrop-filter: blur(50px);
  -webkit-backdrop-filter: blur(50px);
  position: static !important;
  border-radius: 3px;
  width: var(--width);
  padding: 2em;
  background-color: var(--panel-background);
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1);
}
.body-content > p {
  text-align: center;
  font-weight: 600;
  font-size: 12px;
  color: var(--darker-text-color);
}
</style>
