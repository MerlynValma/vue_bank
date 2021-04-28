<template>
  <div>
    <img alt="Vue logo" src="../assets/logo.png">
    <h1 style="color:MediumSeaGreen;">Welcome to MBANK!</h1>
    <br>
    <h3>Get your acccount balance:</h3>
    <input v-model="accountNr" placeholder="Insert your account nr"/>
    <button v-on:click="bank()">Get balance</button>
    {{ balance }}
    <br>
    <h3>Deposit money:</h3>
    <input v-model="amount1" placeholder="Insert amount"/>
    <button v-on:click="depositMoney()">Deposit money</button>
    {{ deposit }}
    <br>
    <h3>Withdraw money:</h3>
    <input v-model="amount2" placeholder="Insert amount"/>
    <button v-on:click="withdrawMoney()">Withdraw money</button>
    {{ withdraw }}
    <br>
    <h3>Transfer money:</h3>
    <input v-model="accountNr1" placeholder="From account"/>
    <br>
    <br>
    <input v-model="accountNr2" placeholder="To account"/>
    <br>
    <br>
    <input v-model="amount3" placeholder="Insert amount"/>
    <button v-on:click="transferMoney()">Transfer money</button>
    {{ transfer }}
    <br>
    <br>
    <h3>Close or activate your account:</h3>
    <button v-on:click="closeAccount()">Close account</button>  <input v-model="accountNr5" placeholder="Insert your account nr"/> <button v-on:click="activeAccount()">Active account</button>
    <br>
    <h3>All transactions:</h3>
    <input v-model="accountNr4" placeholder="Insert your account nr"/>
    <button v-on:click="transactions()">Transactions</button>
    <div align="center">
      <br>
            <table border="1">
      <tr>
        <th>Balance</th>
        <th>Selgitus</th>
      </tr>
      <tr v-for="allTransactions in transaction">
        <td>{{ allTransactions.balance }}</td>
        <td>{{ allTransactions.selgitus }}</td>
      </tr>
    </table>
      </div>
    <br>


  </div>
</template>
<script>

export default {
  data: function () {
    return {
      'accountNr': "",
      'balance': "",
      'deposit': "",
      'amount1': "",
      'withdraw': "",
      'amount2': "",
      'transfer': "",
      'accountNr1': "",
      'accountNr2': "",
      'amount3': "",
      'selgitus': "",
      'id': "",
      'accountNr4': "",
      'accountNr5': "",
      'transaction': []

    }
  },

  methods: {
    "activeAccount": function () {
      this.$http.get('http://localhost:8080/Bank/accountActive/'+ this.accountNr5);
    },
    "closeAccount": function () {
      this.$http.get('http://localhost:8080/Bank/accountClose/'+ this.accountNr5);
    },
    'bank': function () {
      this.$http.get('http://localhost:8080/Bank/getBalance/' + this.accountNr)
          .then(response => {
            console.log(response);
            this.balance = response.data
          });
    },
    'depositMoney': function () {
      this.$http.get('http://localhost:8080/Bank/deposit/' + this.accountNr + "/" + this.amount1)
          .then(response => {
            console.log(response);
            this.deposit = response.data
          });
    },
    'withdrawMoney': function () {
      this.$http.get('http://localhost:8080/Bank/withdraw/' + this.accountNr + "/" + this.amount2)
          .then(response => {
            console.log(response);
            this.withdraw = response.data
          });
    },
    'transferMoney': function () {
      this.$http.get('http://localhost:8080/Bank/transfer/' + this.accountNr1 + "/" + this.amount3 + "/" + this.accountNr2)
          .then(response => {
            console.log(response);
            this.transfer = response.data
          });
    },
    'transactions': function () {
      this.$http.get('http://localhost:8080/Bank/transactions/' + this.accountNr4)
          .then(response => this.transaction = response.data);
    }
  }
}

</script>
<style scoped>

</style>