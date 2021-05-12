<template>
    <main id="Main" >
        <Search @invio="importQ">
        </Search>
        <ul>
        film
        <Scheda :lista="el" v-for="(el,index) in film"  :key="index"> 
                {{el}}{{index}}
        </Scheda>
        tv
        <Scheda :lista="el" v-for="(el,index) in tv"  :key="index"> 
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
            tv:{},
            film:{},
            query:'',

        }
    },
    methods:{
        getData(){ 
            let one = 'https://api.themoviedb.org/3/search/movie?api_key=49b7715adeda3f2ed02386b0db03af61&query='+this.query
            let two = 'https://api.themoviedb.org/3/search/tv?api_key=49b7715adeda3f2ed02386b0db03af61&query='+this.query
            
            
            const requestOne = axios.get(one);
            const requestTwo = axios.get(two);
            
            
            axios.all([requestOne, requestTwo]).then(axios.spread((...responses) => {
            const responseOne = responses[0]
            const responseTwo = responses[1]
            console.log("res1",responseOne)
            console.log("res2",responseTwo)
            console.log("responses",responses[0].data.results);
            //this.g=responses[0].data.results;
            this.film=responses[0].data.results;
            this.tv=responses[1].data.results;
            console.log("this",this.g);
            
            // use/access the results 
            })).catch(errors => {
                console.log(errors)
            // react on errors.

            })



            /*
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
            });*/
        
            
  },
        importQ(text){
            console.log("text",text);
            this.query = text;
            this.getData();
        }
  },
  created(){
      console.log("created");
      
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