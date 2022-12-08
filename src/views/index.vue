<template lang="pug">
  .payment-page(id="app")
    NavigationDrawer.payment-page__navigation
    FormComponent.payment-page__form
    BookingDetail
</template>


<script>

import NavigationDrawer from "../components/NavigationDrawer.vue"
import FormComponent from "../components/Form.vue"
import BookingDetail from "../components/BookingDetail.vue"



export default {
  name: "PaymentPage",
  components: { FormComponent, BookingDetail, NavigationDrawer },

}
</script>

<style lang="sass">
  .payment-page
    display: flex
    justify-content: space-evenly
    width: 100%
    height: 100%

    &__form
      padding-left: 80px
      align-items: center
      width: 540px
</style>
