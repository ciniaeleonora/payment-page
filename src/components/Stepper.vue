<template lang="pug">
  .stepper
    img.stepper__image(
      alt="no-list-data"
      :src="require('../assets/garuda-indonesia-logo-1.svg')"
    )


    v-stepper.stepper__contain(
      value="3"
      color="#002561"
      flat
      )
      v-stepper-header
        v-stepper-step.pa-2(
          step="1"
          complete
          color="#B2B2B2"
        ) Select
        v-divider

        v-stepper-step(
          step="2"
          complete
          color="#B2B2B2"
          )  Book
        v-divider
        v-stepper-step(
          step="3"
          color="#5DA7DB"
          ) Payment

    span Complete Payment in
      Countdown(color="#FF1E1E" end="December 10, 2022") 
</template>


<script>

import Countdown from 'vuejs-countdown'
export default {
  name: "StepperComponent",

  components: {
    Countdown
  },

  data() {
    const now = new Date();
    const newYear = new Date(now.getFullYear() + 1, 0, 1);

    return {
      time: newYear - now,
    }
  }
  
}
</script>

<style lang="sass">
  .stepper
    padding: 1rem
    width: 100%
    z-index: 100
    margin-top: -50px 
    display: flex
    justify-content: space-between

    &__contain
      width: 800px

    &__button
      margin: 20px


</style>