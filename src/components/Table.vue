<template>
    <div id="table">
        <Hand :cards="opponent.hand" which="opponent" :score="opponent.score"/>
        <Hand :cards="player.hand" :as="as" which="player" :score="player.score"/>
        <Playedtokens :tokens="playedTokens" :playedMoney="playedMoney"/>
    </div>
</template>

<script>
import Playedtokens from './Playedtokens.vue';
import Hand from './Hand.vue'

export default{
    name: 'Table',
    components: { Playedtokens, Hand },
    props: ['playedTokens', 'playedMoney', 'player', 'opponent', 'as']
}
</script>

<style lang="scss">
#table{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    box-sizing: border-box;
    padding-bottom: 140px;
    padding-top: 60px;
    align-items: center;
    background: #23581c;
    position: relative;
    height: 700px;
}
</style>