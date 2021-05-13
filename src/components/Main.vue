<template>
    <main id="Main" >
        <Search 
            @invio="importQ">
        </Search>
        <ul>
            <div class="lista">
                <div class="titolo">
                    {{ (film.length) ? "Film" : "" }}
                </div>   
                <Scheda :lista="el" v-for="(el,index) in film"  :key="'film'+index"> 
                        {{el}}{{index}}
                </Scheda>
            </div>  

        <div class="lista">
            <div class="titolo">            
                {{ (tv.length) ? "Tv" : "" }}
            </div>  
            <Scheda :lista="el" v-for="(el,index) in tv"  :key="'tv'+index"> 
                    {{el}}{{index}}
            </Scheda>
        </div>

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
            best:{},
            query:'',

        }
    },
    methods:{
        getData(){ 
            let Y = new Date().getFullYear();
            let one = 'https://api.themoviedb.org/3/search/movie?api_key=49b7715adeda3f2ed02386b0db03af61&language=it-IT&query='+this.query
            let two = 'https://api.themoviedb.org/3/search/tv?api_key=49b7715adeda3f2ed02386b0db03af61&language=it-IT&query='+this.query
            let three ='https://api.themoviedb.org/3/discover/movie?api_key=49b7715adeda3f2ed02386b0db03af61&primary_release_year='+Y+'&sort_by=popularity.desc&language=it-IT'
             
            const requestOne = axios.get(one);
            const requestTwo = axios.get(two);
            const requestThree = axios.get(three);
            
            
            axios.all([requestOne, requestTwo,requestThree]).then(axios.spread((...responses) => {
            const responseOne = responses[0]
            const responseTwo = responses[1]
            const responseThree = responses[2]
            console.log("res1",responseOne)
            console.log("res2",responseTwo)
            console.log("res3",responseThree)
            console.log("responses",responses[0].data.results);
            //this.g=responses[0].data.results;
            this.film=responseOne.data.results;
            this.tv=responseTwo.data.results;
            this.best=responseThree.data.results;
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
            console.log("import text",text);
            this.query = text;
            this.getData();
        }
    },
    created(){
        console.log("created");      
    }
}
</script>

<style lang="scss">

ul{
    display:flex;
    flex-wrap: nowrap;
    flex-direction:column;
    justify-content: space-evenly;
    .lista{
        display:flex;
        justify-content: space-between;
        overflow: scroll;
        
        
    }
}


</style>