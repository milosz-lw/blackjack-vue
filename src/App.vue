<template>
  <Moneybox :money="money"/>
  <Table :playedTokens="playedTokens" :playedMoney="playedMoney" :playerHand="playerHand" :opponentHand="opponentHand"/>
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
      game: false,
      playerHand: [],
      opponentHand: []
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
    drawCard(hand){
      setTimeout(() => {
        let randPos = this.getRandom(0, this.cards.length - 1)
        hand.push(this.cards[randPos])
        this.cards.splice(randPos, 1)
      }, 500)
    },
    clear(){
      this.money += this.playedMoney
      this.playedMoney = 0
      this.playedTokens = []
    },
    deal(){
      this.game = true
      this.drawCard(this.playerHand)
      setTimeout(()=>{this.drawCard(this.opponentHand)}, 500)
      setTimeout(()=>{this.drawCard(this.playerHand)}, 1000)
      setTimeout(()=>{this.drawCard(this.opponentHand)}, 1500)
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