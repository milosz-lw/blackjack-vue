<template>
    <div class="hand">
        <div v-for="card in cards">
            <div class="front">
                <p>{{ card.num }}</p>
                <img :src="require('../assets/' + card.suit + '.png')">
                <p style="text-align: right;">{{ card.num }}</p>
            </div>
            <div class="back">
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name: 'Hand',
    props: ['cards']
}
</script>

<style lang="scss">
@keyframes cardAppear {
    0% {
        opacity: 0;
        transform: translateY(-10px) rotate(0);
    }
    100% {
        opacity: 1;
        transform: translateY(0) rotate(3deg);
    }
}

.hand{
    display: flex;
    user-select: none;
    > div{
        width: 100px;
        height: 150px;
        margin-left: -15px;
        background: white;
        animation: cardAppear .5s;
        transform: rotate(3deg);
        box-shadow: black 5px 5px 5px;
        border-radius: 5px;
        .hidden{
            display: none;
        }
        .front{
            display: flex;
            flex-direction: column;
            justify-content: space-around;
            align-items: center;
            height: 100%;
            p{
                font-size: 2rem;
                margin: 0;
                width: 80%;
            }
            img{
                height: 50%;
            }
        }
        .back{
            background: url('../assets/back.png');
        }
    }
    
}
</style>