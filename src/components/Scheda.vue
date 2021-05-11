<template>
   <div id="scheda" >
                    
            <li>
                {{lista.title}}
                {{lista.original_title}}
                {{lista.original_language}}
                <img v-if="lista.original_language=='en'" src="img/en.png" alt="en">
                <img v-if="lista.original_language=='it'" src="img/it.png" alt="it">
                <div v-if="lista.original_language!='en'||'it'">{{lista.original_language}}</div>
                {{lista.vote_average}}
                <div class="barra" :style="cssVars" ></div> <!--:style="'width:'+(lista.vote_average*10)+'%'"-->
                
            </li>       
       

   </div>
</template>

<script>
export default {
    name:'Scheda',
    data(){
        return{
            
            
        }

    },
    props:{
        lista:Object,
    },
    computed:{
        cssVars(){
            return{
                '--voto-medio': (this.lista.vote_average*10)+'%',
            }
        }
    }

}
</script>

<style>



img{
    width: 50px;
}

.barra{
    width: var(--voto-medio);
    height: 5px;
    background-color: yellow;
    border: 1px solid green;

}

</style>