<template>
  <div id="mortgage-table">
     <p
      v-if="mortgageNums.loan === null"
      class="empty-table"
    >
    </p>


    <table v-else>

      
      <h4>${{monthlyPayment}} per month </h4>
      <hr>
      <p>{{mortgageNums.loan}} loan at {{mortgageNums.term}} year fixed, {{mortgageNums.rate}} % interest</p>


    </table>
    
  </div>
</template>

<script>
  export default {
    name: 'mortgage-table',
    props: {
        mortgageNums: Object,
        monthlyPayment: Number,
    },
  }
</script>

<style scoped>
button {
  margin: 0 0.5rem 0 0;
}
input {
  margin: 0;
}
.empty-table {
  text-align: center;
}
</style>