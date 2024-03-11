<template>
  <Moneybox :money="money"/>
  <Table :playedTokens="playedTokens" :playedMoney="playedMoney" :player="player" :opponent="opponent"/>
  <Menu :playedMoney="playedMoney" :optionsShown="optionsShown" :game="game" @clear="clear" @deal="deal" @addToken="addToken" @hit="drawCard(this.player, true)" @stand="stand"/>
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
      optionsShown: false,
      player:{
        hand: [],
        score: 0
      },
      opponent:{
        hand: [],
        score: 0
      }
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
    drawCard(which, show){
      let randPos = this.getRandom(0, this.cards.length - 1)
      if(show){
        this.cards[randPos].hidden = false
        which.score += this.cards[randPos].num
      }
      which.hand.push(this.cards[randPos])
      if(this.cards[randPos].left>0){
        this.cards[randPos].left--
      } else {
        this.cards.splice(randPos, 1)
      }
    },
    clear(){
      this.money += this.playedMoney
      this.playedMoney = 0
      this.playedTokens = []
    },
    deal(){
      this.game = true
      this.drawCard(this.player, true)
      setTimeout(()=>{this.drawCard(this.opponent, true)}, 500)
      setTimeout(()=>{this.drawCard(this.player, true)}, 1000)
      setTimeout(()=>{this.drawCard(this.opponent, false)}, 1500)
      setTimeout(()=>{this.optionsShown = true}, 2000)
    },
    stand(){
      this.opponent.hand.forEach((card)=>{
        card.hidden = false
      })
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