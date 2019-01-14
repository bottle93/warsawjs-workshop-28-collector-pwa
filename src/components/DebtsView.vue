<template>
  <div class="debts-view__main">
    <div class="debts-view__add-new-debt">
      <button class="debts-view__btn" @click="open" v-if="!extendModal">Add new debt</button>
      <button class="debts-view__btn" @click="open" v-else>Close</button>
    </div>
    <new-debt v-if="extendModal"/>
    <div
      class="debts-view__debts-list"
      v-if="debts !== null"
      v-for="debt in debts"
      :key="debt.id">
      <debt :debtData='debt'/>
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
      extendModal: false
    }
  },
  methods: {
    open () {
      this.extendModal = !this.extendModal
    }
  },
  mounted () {
    axios.get('http://localhost:3000/debts').then(response => {
      this.debts = response.data.reverse()
    }).catch(err => {
      console.log(err)
    })
  }
}
</script>

<style scoped>
  .debts-view__debts-list {
    margin: 0 15px;
  }
  .debts-view__add-new-debt {
    background-color: #999;
    width: 100%;
    padding: 15px 0;
  }
  .debts-view__btn {
   padding: 15px;
   border: none;
   border-radius: 15px;
 }
</style>
