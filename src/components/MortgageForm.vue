<template>
  <div id="mortgage-form">


    <form @submit.prevent="handleSubmit">
      <label>Loan Amount</label>
       <input
       type="number"
       :class="{ 'has-error': submitting && invalidLoan}"
       v-model="mortgageNum.loan" 
       @focus="clearStatus"
       @keypress="clearStatus"
       />
      <label>Loan Term</label>
       <input 
       type="number"
       :class="{ 'has-error': submitting && invalidTerm }"
       v-model="mortgageNum.term" 
       @focus="clearStatus"
       />
       <label>Interest Rate</label>
       <input 
       type="text"
       :class="{ 'has-error': submitting && invalidRate }"
       v-model="mortgageNum.rate" 
       @focus="clearStatus"
       />

       <p v-if="error && submitting" class="error-message">
         ❗Please fill out all required fields
       </p>
       <p v-if="success" class="success-message">
         ✅ Mortgage Calculated
       </p>

      <button>Calculate Payment</button>

    </form>


  </div>
</template>

<script>
  export default {
    name: 'mortgage-form',
    data() {
      return {
        submitting: false,
        error: false,
        success: false,
        mortgageNum: {
          loan: '',
          term: '',
          rate: '' ,
        },
      }
    },
    methods: {
        handleSubmit() {
          this.submitting = true
          this.clearStatus()

          if (this.invalidLoan || this.invalidTerm || this.invalidRate) {
            this.error = true
            return
          }
          
          this.$emit('calc:mortgage', this.mortgageNum)
          this.mortgageNum = {
            loan: '',
            term: '',
            rate: '', 
          }
          this.error = false
          this.success = true
          this.submitting = false
        },
        clearStatus() {
        this.success = false
        this.error = false
        }
    },
    computed: {
      invalidLoan() {
        return this.mortgageNum.loan === ''
        },
      invalidTerm() {
        return this.mortgageNum.term === ''
        },
      invalidRate() {
        return this.mortgageNum.rate === ''
      },
},

    
  }
</script>

<style scoped>
  form {
    margin-bottom: 2rem;
  }

  [class*='-message'] {
    font-weight: 500;
  }

  .error-message {
    color: #d33c40;
  }

  .success-message {
    color: #32a95d;
  }
</style>