<template>
  <Calculator />
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
  }
}
</script>

<style>
html{
  margin: 0;
  padding: 0;
  overflow: hidden;
}
body{
  margin: 0;
  padding: 0;
  font-family: 'Roboto', sans-serif;
  font-size: 16px;
  color: #fff;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
