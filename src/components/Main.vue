<template>
    <main id="Main" >
        <ul>
            <li v-for="(el,index) in g.data.results" :key="index">
                {{el.original_title}}

            </li>
        </ul>
        

    </main>
  
</template>

<script>
import axios from "axios";
export default {
    name : 'Main',
    data(){
        return {
            g:{},

        }
    },
    methods:{
        getData(){
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=49b7715adeda3f2ed02386b0db03af61&query=nemo')
            .then((response) => {
                // handle success
                console.log("response",response);
                this.g=response;
                console.log("this",this);
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
            .then(function () {
                // always executed
            });
            
  }
  },
  created(){
      console.log("created");
      this.getData();
  }
        
    

}
</script>

<style>

</style>