<template>
<div class="list-font">
    <div :key="champion.id" v-for="champion in champions">
        <Champ :champion="champion" />
    </div>
</div>
    
</template>
<script>
import Champ from './Champ.vue'

export default {
    name: 'Champs',
    props: {
        champions: Array,
    },
    components: {
        Champ,
    }
}
</script>
<style scoped>
    .list-font{
        font-family: Avenir, Helvetica, Arial, sans-serif;
    }
</style>