<template  style="margin:0; padding:0;">
<div>
  <Header title="Definitely not Bitcoin price update page" />
  <div>
      <span class="common" style="width: 100px">Updated Time</span><span style="common"> : {{ post2.time.updated }}</span>
  </div>
  <div>
      <span class="common" style="width: 100px">* Disclaimer *</span><span style="common"> : {{ post2.disclaimer }}</span>
  </div>
  <div class="container" style="background-color: skyblue;">
    <Champs :champions="champions" />
    
    <div 
        v-for="post in post" :key="post.code"
        style="font-family: Helvetica; margin: 10px" 
        class="currency">
        <div style="font-weight: bold">BTC to {{ post.description }} </div>
        <div>
          1 BTC => <span v-html="post.symbol"></span> {{ post.rate }}
        </div>
    </div>
    <div style="margin: 10px; margin-top: 150px">
      <span>For more information about crypto, go to <a class="hyperlink" href="https://www.coindesk.com/" target="_blank">Coindesk</a></span>
    </div>
  </div>
  <Footer />
</div>
  
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Champs from './components/Champs.vue'
import axios from 'axios'
//import VueAxios from 'vue-axios'


export default {
  name: 'App',
  components: {
    Header,
    Footer,
    Champs,
  },
  data(){
    return{
      infos: [],
      currecncy: null,
      post: null,
      post2: null,
    }
  },
  mounted(){
     axios
     .get('https://api.coindesk.com/v1/bpi/currentprice.json')
     .then(response => {
        this.post = response.data.bpi, 
        this.post2 = response.data
     })
  },
  async created(){
    try{
      //const url = 'http://ddragon.leagueoflegends.com/cdn/11.16.1/data/en_US/champion/Akali.json'
      //const res = await axios.get(url);
      //const result = res.data.result
      //this.infos = result.map(info =>({
      //  skin: info
      //}))
      
    }catch(e){
      console.error(e);
    }
  },
  filters:{

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container{
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid skyblue;
  padding: 30px;
  border-radius: 10px;
}
.btn{
  display: inline-block;
  border: none;
  color: white;
  padding: 2px 20px;
  margin: 5px;
  cursor: pointer;
  border-radius: 10px;
  font-size: 15px;
  font-family: inherit;
  border: solid black;
}
.common{
  margin: 10px;
  font-weight: bold;
}
.hyperlink{
  font-weight: bold;
  text-decoration: none;
  color: goldenrod;
}
</style>
