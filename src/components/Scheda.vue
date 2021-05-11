<template>
   
                    
            <li id="scheda">
                {{lista.title}}
                {{lista.original_title}}
                <img v-if="lista.original_language=='en'" src="img/en.png" alt="en">
                <img v-else-if="lista.original_language=='it'" src="img/it.png" alt="it">
                <div v-else>{{lista.original_language}}</div>
                {{lista.vote_average}}
                <div class="barra" :style="cssVars" ></div> <!--:style="'width:'+(lista.vote_average*10)+'%'"-->
                
            </li>       
       

   
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
                '--voto-medio': (this.lista.vote_average*5)+'%',
            }
        }
    }

}
</script>

<style scoped lang="scss">


img{
    width: 50px;
}

li{ 
    display: flex;
    justify-content: flex-start;
    flex-basis: calc(100vw / 4);
    flex-wrap: wrap;
    margin: 5px;
    border: 1px solid green;
    border-radius: 5px;    
    background: greenyellow;
        .barra{
        width: var(--voto-medio);
        height: 16px;
        background-color: yellow;
        border: 1px solid green;
        
    }
}


</style>

/*
esempio img https://image.tmdb.org/t/p/w500/u1z05trCA7AuSuDhi365grwdos1.jpg
 */