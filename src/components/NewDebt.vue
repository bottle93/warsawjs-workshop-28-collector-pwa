<template>
    <div class="new-debt__main">
      <input class="new-debt__debt-title new-debt__input" type="text" v-model="title" placeholder="Add description">
      <input class="new-debt__debt-who new-debt__input" type="text" v-model="who" placeholder="Who payed">
      <input class="new-debt__debt-amount new-debt__input" type="number" v-model="amount" placeholder="Amount">
      <button class="new-debt__btn-submit" v-if="this.title && this.amount > 0 && this.who" @click="submitnewdebt">Submit</button>
    </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      title: null,
      amount: null,
      who: null
    }
  },
  methods: {
    reload () {
      this.$router.go(0)
    },
    submitnewdebt () {
      axios.post('http://localhost:3000/debts', {
        "title": this.title,
        "amount": this.amount,
        "who": this.who
      }).then(function (response) {
        return response
      })
        .catch(function (error) {
          console.log(error)
        })
      this.reload()
    }
  }
}
</script>

<style>
  .new-debt__main {
    min-height: 15vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
  }
  .new-debt__input {
    border: none;
    height: 40px;
  }

</style>
