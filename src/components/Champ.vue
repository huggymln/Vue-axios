<template>
    <div class="task">
        <h3>
            {{ champion.name }}
            <i class="fas fa-times"></i>
        </h3>
        <p>{{ champion.class }}</p>
    </div>
</template>
<script>
export default {
    name: 'Champ',
    props: {
        champion: Object,
    },
}
</script>
<style scoped>
.fas{
    color: crimson;
}
.task{
    background: cornsilk;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
    
}
.task h3{
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>