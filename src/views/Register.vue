<template>
  <div>
    <input v-model="email" placeholder="enter your email"/>
    <button v-on:click="register()">Register</button>
    <table>
      <tr v-for="email in emails">
        <td>{{email}}</td>
      </tr>
      <td>{{balance}}</td>
    </table>
  </div>
</template>
<script>

export default {
  data: function () {
    return {
      'email': '',
      'emails': ["puustik@gmail.com", "nuustik@gmail.com"],
      'balance': ""
    }
  },
  methods: {
    'register': function () {
      this.$http.get('http://localhost:8080/Bank/getBalance/EE12345678911')
      .then(response => {
        this.balance = response.data
      });
      this.emails.push(this.email);
    }
  }
}
</script>
