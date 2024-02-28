<template>
    <div id="table">
        <Hand :cards="opponentHand"/>
        <Hand :cards="playerHand"/>
        <Playedtokens :tokens="playedTokens" :playedMoney="playedMoney"/>
    </div>
</template>

<script>
import Playedtokens from './Playedtokens.vue';
import Hand from './Hand.vue'

export default{
    name: 'Table',
    components: { Playedtokens, Hand },
    props: ['playedTokens', 'playedMoney', 'playerHand', 'opponentHand']
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