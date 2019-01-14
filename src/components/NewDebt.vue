<template>
    <div class="new-debt__main">
      <input
        class="new-debt__debt-title new-debt__input"
        type="text"
        v-model="title"
        placeholder="Add description">
      <input
        class="new-debt__debt-who new-debt__input"
        type="text"
        v-model="who"
        placeholder="Who payed">
      <input
        class="new-debt__debt-amount new-debt__input"
        type="number"
        v-model="amount"
        placeholder="Amount">
      <button
        class="new-debt__btn-submit"
        :disabled="!(this.title && this.amount > 0 && this.who)"
        @click="$emit('submitNewDebt', $data)">Submit</button>
    </div>
</template>

<script>
export default {
  data () {
    return {
      title: null,
      amount: null,
      who: null
    }
  },
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
    margin: 10px 0 0 0;
    box-shadow: 0 4px 2px -2px gray;
    border-radius: 10px;
    padding: 0 10px;

  }
  .new-debt__btn-submit {
    padding: 15px;
    border: none;
    border-radius: 15px;
    margin: 10px 0;
  }

</style>
