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
      mortgageNums: [
        {
          id: 1,
          loan: '300,000',
          term: '30 years',
          rate: '3.5%',
        },
        {
          id: 2,
          loan: '420,000',
          term: '15 years',
          rate: '2.5%',
        },
        {
          id: 3,
          loan: '600,000',
          term: '30 years',
          rate: '2.8%',
        },
      ],
    }
  },
  methods: {
    calcMortgage(mortgageNum) {
      const lastId = this.mortgageNums.length > 0 ? this.mortgageNums[this.mortgageNums.length - 1].id: 0;
      const id = lastId + 1;
      const newMortgage = { ...mortgageNum, id };

      this.mortgageNums = [...this.mortgageNums, newMortgage];
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
