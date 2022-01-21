<template>
  <ToDo></ToDo>
</template>

<script>
import ToDo from "./components/To_Do.vue";
export default {
  name: "App",
  components: {
    ToDo,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: "Poppins", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  
}
body {
  background: rgb(221, 221, 221);
}
</style>
