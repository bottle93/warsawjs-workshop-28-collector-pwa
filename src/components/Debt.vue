<template>
    <div class="debt__main">
      <p class="debt__title">{{debtData.title}}</p>
      <div>
        <p class="debt__who">{{debtData.who}}</p>
        <p class="debt__amount">${{debtData.amount}}</p>
      </div>
    </div>
</template>

<script>
export default {
  props: ['debtData']
}
</script>

<style>
  .debt__main {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    border-bottom: 1px solid grey;
  }
  .debt__title {align-self: center}

</style>
