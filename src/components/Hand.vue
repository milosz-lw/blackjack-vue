<template>
    <div class="hand">
        <div v-for="card in cards">{{ card.suit }} {{ card.num }}</div>
    </div>
</template>

<script>
export default{
    name: 'Hand',
    props: ['cards']
}
</script>

<style lang="scss">

</style>