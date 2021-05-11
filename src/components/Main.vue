<template>
    <main id="Main" >
        <Search @invio="importQ">
        </Search>
        <ul>
        <Scheda :lista="el" v-for="(el,index) in g.results"  :key="index">
                {{el}}{{index}}
        </Scheda>
        </ul>

    </main>
  
</template>

<script>
import axios from "axios";
import Scheda from "./Scheda.vue";
import Search from "./Search.vue";
export default {
    name : 'Main',
    components : {
        Scheda,Search,
    },
    data(){
        return {
            g:{},
            query:'',

        }
    },
    methods:{
        getData(){
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=49b7715adeda3f2ed02386b0db03af61&query='+this.query)
            .then((response) => {
                // handle success
                console.log("response",response);
                this.g=response.data;
                console.log("this",this);
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
            .then(function () {
                // always executed
            });
            
  },
        importQ(text){
            console.log(text);
            this.query = text;
            this.getData();
        }
  },
  created(){
      console.log("created");
      this.getData();
  }
        
    

}
</script>

<style>

ul{
    display:flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    
}


</style>