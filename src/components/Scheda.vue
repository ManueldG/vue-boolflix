<template>
   
                    
            <li id="scheda">
                <img :src="'https://image.tmdb.org/t/p/w500'+lista.poster_path" alt="en">
                {{lista.title||lista.name}}
                {{lista.original_title}}
                <div v-if="lista.original_language=='en'">🇬🇧<img  src="img/en.png" alt="en"></div>
                <div v-else-if="lista.original_language=='it'">🇮🇹<img  src="img/it.png" alt="it"></div>
                <div v-else>{{lista.original_language}}</div>
                {{lista.vote_average}}
                <div class="vote">
                    <div class="stars" :style="cssVars">
                        <span class="material-icons-two-tone">
                        star star star star star
                        </span>
                    </div>
                    <!--<div class="barra" :style="cssVars" ></div> :style="'width:'+(lista.vote_average*10)+'%'"-->
                </div>
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
                '--voto-medio': (this.lista.vote_average*10)+'%',
            }
        }
    }

}
</script>

<style scoped lang="scss">



img{
    width: 50px;
    height: 25px;
}

.vote{
    :root {
    --sfondo-scheda: greenyellow;
}
    position: relative;
    .stars{

        background-image: linear-gradient(yellow,yellow);
        background-size: var(--voto-medio) 100%;
        background-repeat: no-repeat;
        color: transparent;
        background-clip: text;
        -moz-background-clip: text;
        -webkit-background-clip: text;
    
        background-color: var(--sfondo-scheda);
        
        z-index: 1;
        
    }
    .barra{
        position: absolute;
        top: 0;
        z-index: 0;
    }
}

li{ 
    display: flex;
    justify-content: flex-start;
    flex-basis: calc(100vw / 4);
    flex-wrap: wrap;
    margin: 5px;
    border: 1px solid;
    border-radius: 5px;    
    background: var(--sfondo-scheda);
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