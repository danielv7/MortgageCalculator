<template>
  <div id="mortgage-table">
     <p
      v-if="mortgageNums.loan === null"
      class="empty-table"
    >
    </p>


    <table v-else>

      <thead>
        <tr>
          <th>Loan</th>
          <th>Term</th>
          <th>Rate</th>
        </tr>
        
      </thead>
      
      <tbody>
        <tr>
          <td>{{ mortgageNums.loan }}</td>
          <td>{{ mortgageNums.term }}</td>
          <td>{{ mortgageNums.rate }}</td>
        </tr>
      </tbody>

      <tr>
        <th>Monthly Payment</th>
      </tr>

      <tbody>
        <tr>{{monthlyPayment}}</tr>
      </tbody>


      



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