<template>
    <div id="playedtokens">
        <div v-for="token in tokens" :style="{background: token.color, top: token.top, left: token.left}">{{ token.value }}</div>
    </div>
    <div v-if="playedMoney" class="playedmoney" style="bottom: .5%">
        <p>{{ playedMoney }}</p>
        <img src="../assets/coin.png">        
    </div>
    <div v-else class="playedmoney" style="bottom: 5%">
        <h1>Place your bet</h1>
    </div>
</template>

<script>
export default{
    name: "Playedtokens",
    props: ['tokens', 'playedMoney']
}
</script>

<style lang="scss">
@keyframes tokenAppear {
    0% {
        opacity: 0;
        transform: translateY(-10px);
    }
    100% {
        opacity: 1;
        transform: translateY(0);
    }
}

#playedtokens{
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;
    color: white;
    font-size: 1.3rem;
    position: absolute;
    left: 50%;
    bottom: 5%;
    z-index: 500;
    width: 80px;
    height: 80px;
    transform: translateX(-50%);
    div{
        position: absolute;
        display: flex;
        justify-content: center;
        align-items: center;
        color: white;
        font-size: 2rem;
        outline: 5px dashed white;
        outline-offset: -10px;
        width: 80px;
        height: 80px;
        border-radius: 40px;
        user-select: none;
        animation: tokenAppear .5s;
    }
    p{
        position: absolute;
        margin: 0;
        bottom: -40%;
    }
}

.playedmoney{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 5px;
    font-size: 1.3rem;
    color: white;
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    height: 25px;
}
</style>