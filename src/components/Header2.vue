<template>
  <header id="Header">
      <img src="/img/MdGPlay.png" alt="LOGO">
      <Search 
         @invio="importQ" >  
      </Search>
      
  </header>
</template>

<script>

import Search from "./Search.vue";

export default {
  data(){
    return{
      query:'',
    }
  },
  props: {
    text: String
  },
  components: {
    Search
  },
  methods: {
    importQ(text){
            console.log("import text",text);
            this.query = text;
            this.$emit('invio',text);
        }
  }

}
</script>

<style scoped lang="scss">

  #Header{
    display:flex;
    justify-content: flex-start;

    img{
      width: 200px;
      height: 111px;
      object-fit: contain;
      object-position: 50% 50%;
      
    }
    
  }
  
</style>