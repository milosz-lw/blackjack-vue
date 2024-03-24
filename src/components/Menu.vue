<template>
    <div id="menu">
        <div class="buttons-container" v-if="optionsShown">
            <button name="stand" @click="stand">Stand</button>
            <button name="hit" @click="hit">Hit</button>
        </div>
        <div id="tokens">
            <div v-for="token in tokens" :style="{background: token.color}" @click="addToken(token)">{{ token.value }}</div>
        </div>
        <div class="buttons-container" v-if="playedMoney && !game">
            <button name="clear" @click="clear">Clear</button>
            <button name="deal" @click="deal">Deal</button>
        </div>
    </div>
</template>

<script>
export default{
    name: 'Menu',
    props: ['playedMoney', 'game', 'optionsShown'],
    data(){
        return{
            tokens:[
                {value: 5, color: '#E03A3A'},
                {value: 10, color: '#3962DD'},
                {value: 50, color: '#39DB82'},
                {value: 100, color: '#D8A43A'},
                {value: 250, color: '#D61DB1'},
                {value: 500, color: '#781DD3'}
            ]
        }
    },
    methods:{
        addToken(token){
            if(!this.game){
                this.$emit("addToken", token)
            }
        },
        clear(){
            this.$emit("clear")
        },
        deal(){
            this.$emit("deal")
        },
        stand(){
            this.$emit("stand")
        },
        hit(){
            this.$emit("hit")
        }
    }
}
</script>

<style lang="scss">
$transition: .2s all ease-in-out;

#menu{
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 15px;
    margin-top: 8px;
}

#tokens{
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 5px;
    div{
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
        transition: $transition;
        &:hover{
            transform: translateY(-5px);
            cursor: pointer;
        }
    }
}

.buttons-container{
    display: flex;
    gap: 10px;
    button{
        width: 100px;
        height: 60px;
        background: #755a27;
        border: none;
        outline: 5px dashed white;
        outline-offset: -10px;
        border-radius: 15px;
        color: white;
        font-size: 1.4rem;
        transition: $transition;
        &:hover{
            transform: translateY(-5px);
            cursor: pointer;
        }
    }
}
</style>