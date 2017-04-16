<template>
 
  <div id="app">
  <h1>Monthly budget</h1>
  <div class="container">
  
   <div class="column-one">
    <h2>Income</h2>
      <label>Monthly Income: </label>
      <input type="text"v-model.number="income">
   </div>

   <div class="column-two">
    <h2>Expenses</h2>
    <h3>Housing/ Living: </h3>
    <label>Rent:</label>
    <input type="text" v-model.number="rent"><br>

    <label>Utilities:</label>
    <input type="text" v-model.number="util"><br>
   
    <label>Home/Renters Insurance:</label>
    <input type="text" v-model.number="rentInsure"><br>

    <label>Child Care:</label>
    <input type="text" v-model.number="childCare"><br>

    <label>Groceries:</label>
    <input type="text" v-model.number="groceries"><br>

    <label>Misc:</label>
    <input type="text" v-model.number="miscHome">
   
    <h3>Loans / Credit Cards:</h3>
    <label>Student Loans:</label>
    <input type="text" v-model.number="studentLoans"><br>

    <label>Credit Cards:</label>
    <input type="text" v-model.number="creditCards"><br>

    <label>Misc:</label>
    <input type="text" v-model.number="miscDebt"><br>

    <h3>Savings: </h3>
    <label>Saving:</label>
    <input type="text" v-model.number="saving"><br>

    <h3>Miscellaneous:</h3>

    <label>Entertainment:</label>
    <input type="text" v-model.number="entertainment"><br>

    <label>Clothing:</label>
    <input type="text" v-model.number="clothing"><br>

    <label>Personal Care:</label>
    <input type="text" v-model.number ="personal"><br>
   </div>

   <div class="column-three">
      <h2>Total</h2>
      <button @click="calc">Calculate</button><br>
      <span>Total monthly income: $</span>{{ income }} <br>
      <span>Total monthly expenses: $</span>{{totalExpenses}} <br>
      <span>Difference: $</span> {{diff}}


   </div> 
   </div><!-- end .container -->
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      income: null,
      rent: null,
      util: null,
      rentInsure: 0,
      childCare: 0,
      groceries: 0,
      miscHome: 0,
      studentLoans: 0,
      creditCards: 0,
      miscDebt: 0,
      saving: 0,
      entertainment: 0,
      clothing: 0,
      personal: 0,
      totalExpenses: 0,
      diff: 0,
    }
  },
   methods: {
      calc() {
        let t  = this;
        t.totalExpenses = t.rent + t.util + t.rentInsure + t.childCare + t.groceries + t.miscHome + t.studentLoans + t.creditCards + t.miscDebt + t.saving + t.entertainment + t.clothing + t.personal;

        t.diff =t.income - t.totalExpenses;


      }
    }
}
</script>

<style lang="scss">
// defaults 
body {
  padding: 0;
  margin: 0;
}

a {
  text-decoration: none;
  color: inherit;
}
h1, h2 {
  text-align: center;
}


#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 30px;
}

.container {
  display: grid;
  grid-template-columns: 33vw 33vw 32vw;


  .column-one {
    margin-left: 5vw;
  }
}

</style>
