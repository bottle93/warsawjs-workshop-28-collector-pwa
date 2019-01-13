<template>
  <div class="debts-view__main">
    <div class="debts-view__debts-list" v-if="debts !== null" v-for="debt in debts" :key="debt.id">
      <debt :debtData='debt'/>
    </div>
    <div class="debts-view__add-new-debt" v-on:click="addNew = !addNew" v-if="!addNew"><p>+</p></div>
    <div v-if="addNew">
      <new-debt/>
    </div>
  </div>
</template>

<script>
import Debt from './Debt'
import NewDebt from './NewDebt'
import axios from 'axios'
export default {
  name: 'CollectorPWA',
  components: {Debt, NewDebt},
  data () {
    return {
      debts: null,
      addNew: false
    }
  },
  mounted () {
    axios.get('http://localhost:3000/debts').then(response => {
      this.debts = response.data
    }).catch(err => {
      console.log(err)
    })
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.debts-view__main {
  margin-bottom: 110px;
}
.debts-view__add-new-debt {
  bottom: 20px;
  right: 10px;
  margin: 0;
  position: fixed;
  font-size: 5em;
  font-weight: 800;
  color: red;
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background-color: white;
  box-shadow: inset 0 0 15px lightgray;
}
.debts-view__add-new-debt p {
  margin: 0;
}
</style>
