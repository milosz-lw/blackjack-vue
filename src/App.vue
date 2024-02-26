<template>
  <Moneybox :money="money"/>
  <Table/>
  <Menu/>
</template>

<script>
import cardsJson from './assets/cards.json'

import Menu from './components/Menu.vue'
import Table from './components/Table.vue'
import Moneybox from './components/Moneybox.vue'

export default {
  name: 'App',
  components: { Table, Moneybox, Menu },
  data(){
    return{
      //table of cards:
      cards: cardsJson.cards,
      usedCards: [],
      money: 1000
    }
  }
}
</script>

<style lang="scss">
html, body{
  background: #eee;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
img{
  max-height: 100%;
  max-width: 100%;
}
</style>