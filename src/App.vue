<template>
  <div id="app">
    <Header :invio="querys" @invio="querys">

    </Header>
    <Main :text="query">
    </Main>
    <Footer/>
  </div>
</template>

<script>
import Main from './components/Main.vue'
import Header from './components/Header2.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  data(){
    return{
      query:'',
    }
  },
  props: {
    text: String
  },
  components: {
    Main,Header,Footer
  },
  methods:{
  querys(text){
    this.query = text;
  }
}
}

</script>

<style lang="scss">
#app {
  box-sizing: border-box;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
