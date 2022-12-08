<template lang="pug">

  v-card
    ul
      li(v-for="navigation in navigations")
        a(:class="navigation.status" href="#") {{ navigation.title }}
</template>

<script>
export default {
  name: "NavigationDrawer",

  data: () => ({
    navigations: [
      { id: 1, title: "Credit/Debit Card" , link: "", status: "active"},
      { id: 2, title: "LinkAja", link: "", status: ""},
      { id: 3, title: "KlikBCA", link: "", status: ""},
      { id: 4, title: "e-Pay BRI", link: "", status: ""},
      { id: 5, title: "CIMB Clicks", link: "", status: ""},
      { id: 6, title: "GoPay", link: "", status: ""},
      { id: 7, title: "ATM", link: "", status: ""},
      { id: 8, title: "BNI Mobile", link: "", status: ""},
      { id: 9, title: "ShopeePay", link: "", status: ""},
      { id: 10, title: "Bank Transfer", link: "", status: ""},
      { id: 11, title: "Alfamart", link: "", status: ""},
      { id: 12, title: "Indomaret", link: "", status: ""}
    ]
  }),
}
</script>

<style lang="sass" scoped>
  h4
    color: #0078AA
    
  ul
    list-style-type: none
    margin: 0
    padding: 0
    width: 160px
    position: fixed
    height: 100%
    overflow: auto

  li a 
    display: block
    color: #000
    padding: 8px 16px
    text-decoration: none

  li a.active 
    background-color: #5DA7DB
    color: white


  
</style>