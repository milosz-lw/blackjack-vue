<template>
    <div id="table">
        <Playedtokens :tokens="playedTokens"/>
    </div>
</template>

<script>
import Playedtokens from './Playedtokens.vue';

export default{
    name: 'Table',
    components: {Playedtokens},
    props: ["playedTokens"]
}
</script>

<style lang="scss">
#table{
    background: #23581c;
    position: relative;
    height: 700px;
}
</style>