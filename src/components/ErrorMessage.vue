<template>
  <div class="error-message-wrapper">
    <div class="error-title-wrapper">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        height="24px"
        viewBox="0 0 24 24"
        width="24px"
        fill="#FF033E"
      >
        <path
          d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 11c-.55 0-1-.45-1-1V8c0-.55.45-1 1-1s1 .45 1 1v4c0 .55-.45 1-1 1zm1 4h-2v-2h2v2z"
        />
      </svg>
      <h1>Error</h1>
    </div>
    <p>Please enter a name for the task!</p>
  </div>
</template>

<script>
export default {
  name: "ErrorMessage",
};
</script>

<style>
.error-message-wrapper {
  margin: 0.5em 0 0;
  background-color: var(--panel-background);
  padding: 1em;
  border-radius: 3px;
}
.error-title-wrapper {
  display: flex;
  align-items: center;
}
.error-title-wrapper > h1 {
  font-size: 18px;
  font-weight: 600;
  margin: 0 0 0 0.5em;
  color: var(--text-color);
}
.error-message-wrapper > p {
  margin: 0.5em 0 0;
  font-size: 12px;
  color: var(--text-color);
  font-weight: 300;
}
</style>
