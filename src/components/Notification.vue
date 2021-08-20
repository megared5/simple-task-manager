<template>
  <div
    :class="[
      showNotification ? 'notification-visible' : '',
      'notification-wrapper',
    ]"
  >
    <div class="notification-title-wrapper">
      <div class="notification-title">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          height="24px"
          viewBox="0 0 24 24"
          width="24px"
          fill="#00000"
        >
          <path d="M0 0h24v24H0V0z" fill="none" />
          <path
            d="M9 16.2l-3.5-3.5c-.39-.39-1.01-.39-1.4 0-.39.39-.39 1.01 0 1.4l4.19 4.19c.39.39 1.02.39 1.41 0L20.3 7.7c.39-.39.39-1.01 0-1.4-.39-.39-1.01-.39-1.4 0L9 16.2z"
          />
        </svg>
        <h1>{{ notificationMessage.notificationTitle }}</h1>
      </div>
      <button
        class="close-notification-button"
        @click="
          () => {
            showNotification = false;
          }
        "
      >
        ×
      </button>
    </div>
    <p>{{ notificationMessage.notificationMessage }}</p>
  </div>
</template>

<script>
export default {
  name: "Notification",
  props: {
    showNotification: Boolean,
    notificationMessage: Object,
  },
};
</script>

<style>
.notification-wrapper {
  backdrop-filter: blur(50px);
  -webkit-backdrop-filter: blur(50px);
  border: var(--border);
  opacity: 0;
  position: fixed;
  right: 50px;
  bottom: 50px;
  border-radius: 3px;
  background-color: var(--panel-background);
  padding: 1em;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1);
}
.notification-visible {
  opacity: 1;
}
.notification-title-wrapper {
  justify-content: space-between;
  display: flex;
  align-items: center;
}
.notification-title {
  display: flex;
  align-items: center;
}
.notification-title > svg {
  fill: var(--theme-color);
}
.notification-title > h1 {
  font-weight: 300;
  color: var(--text-color);
  font-size: 18px;
  margin: 0 0 0 0.5em;
}
.notification-wrapper > p {
  color: var(--darker-text-color);
  font-size: 12px;
}
.close-notification-button {
  cursor: pointer;
  border-radius: 3px;
  background-color: var(--item-background);
  color: var(--text-color);
  margin-left: 2em;
  float: right;
  padding: 0.5em 1em;
  border: var(--border);
}
.close-notification-button:hover {
  color: var(--button-hover-color);
  background-color: var(--theme-color);
}
.close-notification-button:active {
  background-color: var(--darker-theme-color);
}
</style>
