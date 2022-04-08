<template>
  <div id="app"></div>
</template>

<script>
export default {
  name: "App",
  components: {},
};
const result = [];
const axios = require("axios").default;
axios
  .get("https://flynn.boolean.careers/exercises/api/array/music")
  .then((resp) => {
    result.push(resp.data.response);
  });

console.log(result);
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
