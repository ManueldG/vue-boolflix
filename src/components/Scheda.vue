<template>
   
                    
            <li id="scheda"  :style="cssVars">
                <div class="lato-a">
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
                </div>
                <div class="lato-b">
                    <img :src="'https://image.tmdb.org/t/p/w500'+lista.poster_path" alt="en">
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
                '--sfondo-scheda': 'greenyellow'
            };
        }
    }

}
</script>

<style scoped lang="scss">


li#scheda{
    position:relative;
    height: 200px;
    width: 100px;
    margin: 5px;
    border: 1px solid;
    border-radius: 5px;    
    background: var(--sfondo-scheda);

    .lato-a{  
        position:absolute; 
        width:100%;
        height:100%; 
        margin:0;
        top:0;
        background-color: green;
        z-index:1;
        transition: transform 2s , z-index 2s;
        img{
            height: 20px;
            width: 30px;
        }

        .vote{
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
        }
    }   

    .lato-b{  
        position:absolute;
        height: 200px;
        width: 100px;
        top:0;
        background-color: red;
        z-index:0;
        transform: rotateY(180deg);
        transition: transform 2s , z-index 2s;
        img{
            width: 50px;
            height: 25px;
        }
        

    }

    &:hover .lato-b{ 
        transform: rotateY(360deg);
        z-index:1;
    }
    
    &:hover .lato-a{ 
        z-index: 0;
        transform: rotateY(180deg);
    }
    
    
}


</style>

/*
esempio img https://image.tmdb.org/t/p/w500/u1z05trCA7AuSuDhi365grwdos1.jpg
 */