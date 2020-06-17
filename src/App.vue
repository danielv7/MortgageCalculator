<template>
  <div 
    id="app" 
    class="small-container"
  >
    <h1>Mortgage Detials</h1>

    <mortgage-form 
      @calc:mortgage="calcMortgage" 
      />
    <mortgage-table
      :mortgageNums="mortgageNums"
      :monthlyPayment="monthlyPayment"
      />


  </div>
</template>

<script>

import MortgageTable from '@/components/MortgageTable.vue'
import MortgageForm from '@/components/MortgageForm.vue'

export default {
  name: 'App',
  components: {
    MortgageTable,
    MortgageForm,
  },
  data() {
    return {
      mortgageNums: {loan: null, term: null, rate: null},
      monthlyPayment: null,
    }
  },
  methods: {
    calcMortgage(mortgageNum) {
      this.mortgageNums.loan = mortgageNum.loan
      this.mortgageNums.term = mortgageNum.term
      this.mortgageNums.rate = mortgageNum.rate


      const p = parseInt(mortgageNum.loan)
      const n = (parseInt(mortgageNum.term)* 12)
      const r = (parseFloat(mortgageNum.rate)/12)


      this.monthlyPayment = p*(r*((1+r)**n))/(((1+r)**n)-1)
      this.monthlyPayment = Math.round((this.monthlyPayment+ Number.EPSILON) * 100) / 100


      //Calculating Total Interest
      //totalInterest = (monthlyPayment * (term * 12)) - (loan)
      //console.log(totalInterest)

    },
  },
  
  
}

</script>

<style>
button {
  background: #009435;
  border: 1px solid #009435;
}

.small-container {
  max-width: 680px;
}
</style>
