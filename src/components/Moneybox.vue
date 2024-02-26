<template>
    <div id="moneybox">
        {{ money }}
        <img src="../assets/coin.png">
    </div>
</template>

<script>
export default{
    name: 'Moneybox',
    props: ['money']
}
</script>

<style lang="scss">
#moneybox{
    display: flex;
    justify-content: center;
    position: absolute;
    top: 5px;
    left: 5px;
    gap: 5px;
    font-size: 1.3rem;
    align-items: center;
    background: #fafafa;
    width: 100px;
    height: 50px;
    padding: 8px;
    border-radius: 15px;
    user-select: none;
}
</style>