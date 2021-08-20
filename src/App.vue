<template>
  <Body />
</template>

<script>
import Body from "./components/Body.vue";
export default {
  name: "App",
  components: {
    Body,
  },
};
</script>
<style>
/* #region Theme variables */
:root {
  --border: 0px solid #000000;
  --background-image: none;
  --width: 400px;
  --theme-color: #0bad54;
  --darker-theme-color: #0f994d;
  --text-color: #f4f4f4;
  --button-hover-color: #f4f4f4;
  --darker-text-color: #9a9a9a;
  --lighter-panel-background: #4a4a4a;
  --panel-background: #454545;
  --item-background: #353535;
  --lighter-item-background: #3a3a3a;
  --body-background: #2e2e2e;
  --input-hover: #f4f4f41a;
}
.light-theme {
  --border: 0px solid #000000;
  --background-image: none;
  --width: 400px;
  --theme-color: #0b90dd;
  --darker-theme-color: #0b80c4;
  --text-color: #2e2e2e;
  --button-hover-text: #f4f4f4;
  --darker-text-color: #aaaaaa;
  --lighter-panel-background: #ffffff;
  --panel-background: #fafafa;
  --item-background: #f4f4f4;
  --lighter-item-background: #f0f0f0;
  --body-background: #f4f4f4;
  --input-hover: #9090901a;
}
.megared-theme {
  --border: 1px solid #ffffff45;
  --background-image: url("./assets/Mega Red.jpg");
  --width: 600px;
  --theme-color: #ff033ee0;
  --darker-theme-color: #e9073ce0;
  --text-color: #ffffff;
  --button-hover-text: #f4f4f4;
  --darker-text-color: #cecece;
  --lighter-panel-background: #ffffff15;
  --panel-background: #ffffff25;
  --item-background: #ffffff35;
  --lighter-item-background: #ffffff45;
  --body-background: #f4f4f4;
  --input-hover: #ffffff25;
}
.dark-megared-theme {
  --border: 1px solid #00000030;
  --background-image: url("./assets/Mega Red.jpg");
  --width: 600px;
  --theme-color: #ff033ee0;
  --darker-theme-color: #e9073ce0;
  --text-color: #ffffff;
  --button-hover-text: #f4f4f4;
  --darker-text-color: #aeaeae;
  --lighter-panel-background: #00000015;
  --panel-background: #00000025;
  --item-background: #00000035;
  --lighter-item-background: #00000045;
  --body-background: #f4f4f4;
  --input-hover: #ffffff25;
}
/* #endregion */
* {
  transition: all 0.1s;
  font-family: Montserrat;
}
::selection {
  background-color: var(--theme-color);
  color: var(--button-hover-color);
}
body {
  background-image: var(--background-image);
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  padding: 5em;
  margin: 0;
  overflow-x: hidden;
  height: 100%;
  display: flex;
  align-items: center;
  background-color: var(--body-background);
  justify-content: center;
}
</style>
