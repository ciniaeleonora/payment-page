<template lang="pug">
  v-app.form-detail
    h4 CARD DETAILS
    div.mb-3(style="border-bottom:3px dashed #B2B2B2")

    div.form-detail__form
      v-text-field.form-detail__input(
        label="Card Number*"
        v-model="document.cardNumbers"
        :rules="[...fieldRequiredRule, ...cardNumberRules]"
      )

      img.form-detail__input(
        alt="cards"
        :src="require('../assets/Group -1.svg')"
      )

    div.form-detail__form
      v-select.form-detail__input(
        :rules="fieldRequiredRule"
        label="Expiration Date*"
        v-model="document.monthExpire"
        placeholder="Month"
        :items="months"
      )

      v-select.form-detail__input(
        :rules="fieldRequiredRule"
        v-model="document.yearExpire"
        placeholder="Year"
        :items="years"
      )

      v-text-field.form-detail__input(
        :rules="fieldRequiredRule"
        v-model="document.cvcNumber"
        label="CVC*"
        placeholder="000"
      )

    h4(style="#0078AA") BILLING INFORMATION
    div.mb-3(style="border-bottom:3px dashed #B2B2B2")

    div.form-detail__form
      v-text-field.form-detail__input(
        :rules="fieldRequiredRule"
        label="Card Holder Name*"
        placeholder="John Doe"
      )

    div.form-detail__form
      v-text-field.form-detail__input(
        label="Address"
        placeholder="Jl Jendral Sudirman Kav. 10-11"
      )

      v-text-field.form-detail__input(
        label="Country"
        placeholder="Indonesia"
      )

    div.form-detail__form
      v-text-field.form-detail__input(
        label="Province/State"
        placeholder="DKI Jakarta"
      )

      v-text-field.form-detail__input(
        label="City"
        placeholder="Jakarta"
      )

      v-text-field.form-detail__input(
        label="Zip Code"
        placeholder="10202"
      )

    div.form-detail__form
      v-text-field.form-detail__input(
        label="Email"
        placeholder="example@email.com"
      )

      v-text-field.form-detail__input(
        label="Phone"
        placeholder="0812 3456 7890"
      )


    div.mb-3(style="border-bottom:3px dashed #B2B2B2")
    div.form-detail__form
      .form-detail__form-checkbox
        .form-detail__form-checkbox-redeem
          span(style="font-size: 12px;") Reedem Point
          v-icon.tooltip(style="font-size: 12px; margin-left: 5px;") mdi-help-circle  
            span.tooltiptext Tooltip text
        v-checkbox.form-detail__checkbox(v-model="approval")
          template(v-slot:label)
            div(style="font-size: 12px;") I'd like to redeem points from this credit card

      v-select.form-detail__input(
        label="Installment Plan"
        placeholder="No Installment"
        :items="installmentPlans"
      )

    div.form-detail__form
      v-card.form-detail__form-card(
        width="100%"
        outlined
        color="#F6F6F6"
      )
        h5 PRICE DETAILS

        div.form-detail__form-payment-sum
          span Air Transportation Charge
          span {{ paymentInfo.currency }} {{ paymentInfo.price }}

        div.form-detail__form-payment-sum
          span Baggage
          span.form-detail__free-text FREE

        div.form-detail__form-payment-sum
          span Flight Insurance
          span {{ paymentInfo.currency }} {{ paymentInfo.flightInsurance }}

        div.form-detail__form-payment-sum
          span Service Fee
          span {{ paymentInfo.currency }} {{ paymentInfo.serviceFee }}

        v-divider.divider

        div.form-detail__form-payment-sum
          span Total Price
          div
            v-icon.tooltip(style="font-size: 12px; margin-left: 5px; color: #CF0A0A") mdi-alert-circle
            span {{ paymentInfo.currency }} {{ computeTotalPrice }}
        
    v-btn.mt-5(
      outlined
      color="#0078AA"
    ) Use Promo Code

    .payment-button
      v-btn.mt-5(
        dark 
        align-end 
        width="156px"
        color="#0D4C92"
        :disabled="disable"
        @click="onPayment"
      ) Pay Now

  
</template>

<script>

export default {
  name: "FormComponent",

  data: () => ({
    document: {
      cardNumbers: null,
      monthExpire: null,
      yearExpire: null,
      cvcNumber: null,
      cardHolderName: null,
      address: null,
      country: null,
      email: null,
      phone: null
    },
    paymentInfo: {
      currency: "IDR",
      price: 2167000,
      flightInsurance: 60000,
      serviceFee: 11000
    },
    months: ["January","February","March","April","May","June","July","August","September","October","November","December"],
    years: [],
    installmentPlans: ["No Installment", "12-month installment", "66-month installment", "3-month installment"],
    approval: false
  }),

  created() {
    for (let i = new Date().getFullYear(); i < new Date().getFullYear() + 20; i++) {
      this.years.push(i) 
    }
  },

  computed: {
    computeTotalPrice() {
      return this.paymentInfo.price + this.paymentInfo.flightInsurance + this.paymentInfo.serviceFee
    },

    fieldRequiredRule() {
      return [
        val => !!val || "This field is required"
      ]
    },

    cardNumberRules() {
      return [
        val => /^[0-9]+$/.test(val) || "Card number is invalid",
        val => val.length === 16 || "Format is invalid"
      ]
    }
  },

  methods: {
    onPayment() {
      console.log("PAID")
    }
  }
}
</script>


<style lang="sass" scoped>
  h4
    margin-bottom: 10px
    color: #0078AA
    text-align: left

  h5
    text-align: left
    color: #0078AA
    margin-bottom: 5px

  .divider
    margin: 10px 0

  .form-detail
    margin-bottom: 100px
    &__form
      margin-bottom: 5px
      display: flex
      justify-content: space-evenly

    &__input
      margin-top: 5px
      padding: 5px

    &__form-checkbox
      text-align: left

    &__checkbox
      padding-right: 5px
    
    &__form-card
      position: relative
      padding: 20px

    &__form-payment-sum
      font-size: 12px
      display: flex
      justify-content: space-between

    &__free-text
      color: #8BBCCC


  .tooltip
    position: relative
    display: inline-block
    border-bottom: 1px dotted black

  .tooltip .tooltiptext 
    visibility: hidden
    width: 120px
    background-color: black
    color: #fff
    text-align: center
    border-radius: 6px
    padding: 5px 0

    /* Position the tooltip */
    position: absolute
    z-index: 1


  .tooltip:hover .tooltiptext
    visibility: visible
  
  .payment-button
    display: flex
    justify-content: flex-end

</style>

