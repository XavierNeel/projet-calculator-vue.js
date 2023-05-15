<template>

  <div id="app">
    <Calculator></Calculator>

  </div>

</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
  },

  
}

</script>



<style>

@import url('https://fonts.googleapis.com/css2?family=Roboto%3Awght%40300%3B400%3B700&display=swap');

#app {
  font-family: 'Roboto', sans-serif;
}
</style>
