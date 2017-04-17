<template>
 
  <div id="app">
  <h1>Monthly budget</h1>
  <div class="container">
   <div class="column-one">
    <h2>Income</h2>
      <label>Monthly Income: </label>
      <input type="text"v-model.number="income" @keyup="calc()">
   </div>

   <div class="column-two">
    <h2>Expenses</h2>
    <div class="sub-col-one">
    <h3>Housing/ Living: </h3>
    <label>Rent:</label>
    <input type="text" v-model.number="rent" @keyup="calc()"><br>

    <label>Utilities:</label>
    <input type="text" v-model.number="util" @keyup="calc()"><br>
   
    <label>Home/Renters Insurance:</label>
    <input type="text" v-model.number="rentInsure" @keyup="calc()"><br>

    <label>Child Care:</label>
    <input type="text" v-model.number="childCare" @keyup="calc()"><br>

    <label>Groceries:</label>
    <input type="text" v-model.number="groceries" @keyup="calc()"><br>

    <label>Misc:</label>
    <input type="text" v-model.number="miscHome" @keyup="calc()">
   
    <h3>Loans / Credit Cards:</h3>
    <label>Student Loans:</label>
    <input type="text" v-model.number="studentLoans" @keyup="calc()"><br>

    <label>Credit Cards:</label>
    <input type="text" v-model.number="creditCards" @keyup="calc()"><br>

    <label>Misc:</label>
    <input type="text" v-model.number="miscDebt" @keyup="calc()"><br>
    </div>

    <div class="sub-col-two">

    <h3>Savings: </h3>
    <label>Saving:</label>
    <input type="text" v-model.number="saving" @keyup="calc()"><br>

    <h3>Miscellaneous:</h3>

    <label>Entertainment:</label>
    <input type="text" v-model.number="entertainment" @keyup="calc()"><br>

    <label>Clothing:</label>
    <input type="text" v-model.number="clothing" @keyup="calc()"><br>

    <label>Personal Care:</label>
    <input type="text" v-model.number ="personal" @keyup="calc()"><br>
    </div>
   </div>

   <div class="column-three">
      <h2>Total</h2>
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
      income: 0,
      rent: 0,
      util: 0,
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
        let house = t.rent + t.util + t.rentInsure + t.childCare + t.groceries + t.miscHome;
        let loan = t.studentLoans + t.creditCards + t.miscDebt;
        let misc = t.saving + t.entertainment + t.clothing + t.personal;
        t.totalExpenses = house + loan + misc;

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
  background-color: #333;
  color: #ddd;
  margin: 0; 
  padding: 2vh 0;
}

h2 {
  margin-top: 1vh;
  border-radius: 3px;
}


#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  width: 100vw;
  
}

.container {
  width: 55vw;
  margin-left: 15vw;
  display: grid;
  grid-template-columns: 33vw 33vw 32vw;
  grid-template-row: 50vh 50vh;



  .column-two {
    grid-column-start: 1;
    grid-column-end: 3;
    grid-row-start: 2;

    h2 {
      margin-left: 15vw;
    }    


    display: grid;
    grid-template-columns: 50vw 30vw;

    .sub-col-one {
      grid-column-start: 1;
    }

    .sub-col-two {
      grid-column-start: 2;
    }
  }
  .column-three {
    text-align: center;
  }
}

</style>
