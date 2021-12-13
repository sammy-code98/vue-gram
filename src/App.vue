<template>
  <div id="app">
    <phone-body />
    <router-view />
  </div>
</template>

<script>
import PhoneBody from "./components/PhoneSection.vue";
export default {
  name: "App",
  components: {
    "phone-body": PhoneBody,
  },
};
</script>
<style lang="scss" src="./styles/app.scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
