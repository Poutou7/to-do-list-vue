<template>
  <div>
    <HeaderComp />
    <AllTasks />
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue';
import AllTasks from './components/AllTasks.vue'
export default {
  name: "App",
  components: {
    HeaderComp,
    AllTasks,
  }
};
</script>

<style>
@import './assets/font/css/all.min.css';
@import './assets/font/css/normalize.css';

body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #ffecda;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 30px;
  width: 500px;
  box-shadow: 0 3px 10px rgb(151 151 151 / 50%);
  background-color: #fff;
}
</style>
