<template lang="pug">
  v-card.booking-detail(
    height="320px"
    width="320px"
    outlined
    color="primary"
  )
    .booking-detail__row
      h4 YOUR BOOKING
      h4 Details

    div.ma-5(style="border-bottom:3px dotted #B2B2B2")

    .booking-detail__row
      h5 LIST OF PASSANGER(S)

    .booking-detail__row
      span Mr. John Doe
      span Adult

    v-divider

    .booking-detail__row
      h5 FLIGHT

    .booking-detail__row
      div
        v-icon mdi-airplane
        span.booking-detail__text Jakarta (CGK)
        v-icon mdi-arrow-right
        span.booking-detail__text Denpasar (DPS)


    .booking-detail__row
      v-icon mdi-calendar
      span.booking-detail__text 25 Desember 2022

    v-divider

    .booking-detail__row
      h5 PRICE

    .booking-detail__row
      span Total
      div
        v-icon(style="font-size: 12px; margin-left: 5px;") mdi-alert-circle
        span IDR 2238000

</template>

<script>
export default {
  name: "BookingDetail"
}
</script>

<style lang="sass">
  h4
    color: #0078AA


  .booking-detail
    padding: 10px
    margin-top: 88px

    &__row
      margin: 10px
      display: flex
      justify-content: space-between

    &__text
      margin: 5px

</style>