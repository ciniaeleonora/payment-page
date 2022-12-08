<template lang="pug">
  div(id="app")
    StepperComponent
    PaymentPage(msg="Welcome to Your Vue.js App")
  </div>
</template>

<script>
import PaymentPage from './views'
import StepperComponent from "./components/Stepper.vue"

export default {
  name: 'App',
  components: {
    PaymentPage,
    StepperComponent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
