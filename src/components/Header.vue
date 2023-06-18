<template>
    <header class="header">
        <h1>{{title}}</h1>
        <div ref="clock" class="clock"></div>
    </header>
</template>

<script>
//import Button from './Button.vue'

export default {
    name: 'Header',
    props: ['title'],
    components:{
        //Button,
    },
    methods: {
        check(i){
            if(i < 10){
                i = "0" + i;
                return i;
            }else
            return i;
        },
        timer(){
            const today = new Date();
            let h = today.getHours();
            let m = today.getMinutes();
            let s = today.getSeconds();
            m = this.check(m); s = this.check(s);
            this.$refs.clock.textContent = h +":"+ m +":"+ s;
            setTimeout(this.timer, 1000);
        }
    },
    mounted(){
        this.timer();
    }
}
</script>
<style scoped>
    .header{
        text-align: center;
        font-family: Avenir, Helvetica, Arial, sans-serif;
        margin: auto;
    }
    .center{
        text-align: center;
    }
    .clock{
        font-size: 45px;
        margin: 10px;
        font-weight: bold;
    }
</style>