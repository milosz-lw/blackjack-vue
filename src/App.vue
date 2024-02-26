<template>
  <Moneybox :money="money"/>
  <Table :playedTokens="playedTokens" :playedMoney="playedMoney"/>
  <Menu :playedMoney="playedMoney" :game="game" @clear="clear" @deal="deal" @addToken="addToken"/>
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
      money: 1000,
      playedMoney: 0,
      playedTokens: [],
      game: false
    }
  },
  methods:{
    getRandom(min, max){
      return Math.floor(Math.random() * (max - min + 1)) + min
    },
    addToken(token){
      if(this.money>=token.value){
        this.money -= token.value
        this.playedMoney += token.value
        token.top = `${this.getRandom(-5, 5)}%`
        token.left = `${this.getRandom(-5, 5)}%`
        this.playedTokens.push(token)
      }
    },
    clear(){
      this.money += this.playedMoney
      this.playedMoney = 0
      this.playedTokens = []
    },
    deal(){
      this.game = true
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