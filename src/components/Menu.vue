<template>
    <div id="menu">
        <div id="tokens">
            <div v-for="token in tokens" :style="{background: token.color}">{{ token.value }}</div>
        </div>
    </div>
</template>

<script>
export default{
    name: 'Menu',
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
    }
}
</script>

<style lang="scss">
$transition: .2s all ease-in-out;

#menu{
    margin-top: 8px;
}
#tokens{
    display: flex;
    justify-content: center;
    align-items: center;
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
</style>