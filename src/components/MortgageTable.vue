<template>
  <div id="mortgage-table">
    <table>

        <thead>
            <tr>
                <th>Loan</th>
                <th>Term</th>
            </tr>
      </thead>
      
      <tbody>
        <tr v-for="mortgageNum in mortgageNums" :key="mortgageNum.id">
          <td>{{ mortgageNum.loan }}</td>
          <td>{{ mortgageNum.term }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  export default {
    name: 'mortgage-table',
    props: {
        mortgageNums: Array
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